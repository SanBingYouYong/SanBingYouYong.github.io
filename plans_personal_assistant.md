# Goal

An LLM-based personal planning and scheduling assistant that can help users to manage their daily tasks and appointments. The assistant reads a default schedule for the week from `weekly_schedule.md` and can also be promtped to add, delete, or update tasks and appointments. The assistant can also be asked to provide a summary of the day's tasks and appointments by `brief me on my day` command (with a date timestamp).

## Design

The following data model are to be maintained by the assistant and optionally also the user:

- Default Weekly Schedule
  - The default weekly schedule is stored in `weekly_schedule.md` and is read by the assistant when needed.
- Temporary Schedule
  - The assistant also maintains a list of temporary, sudden, or one-time tasks added per user request. It will maintain them in `temp_tasks.md` and will read and write to this file as needed.
- User Notes
  - A list of user specified short text notes about tasks or user preferences that the assistant should remember. These notes are stored in `user_notes.md` and are read and written to as needed.

The following tasks are to be performed by the assistant, and the process is broken down into multiple agents to ensure correctness:

- Brief me on my day
  - The assistant should provide a summary of the day's tasks and appointments on a given date.
  - Process: `Interpreter` identifies user request as this task, `Reader`s reads data models and returns relevant information, `Aggregator` combines and format the information, and `Briefer` presents the information to the user.
- Remind me the rest of the day
  - The assistant should remind the user of the remaining tasks and appointments for the day at a given time.
  - Process: `Interpreter` identifies user request as this task, `Reader`s reads data models and returns relevant information, `Aggregator` combines and format the information, and `Briefer` presents the information to the user.
- Update my schedule
  - The assistant should update the schedule with the user's input: add, delete, or update items on the schedule.
  - Process: `Interpreter` identifies user request as this task, `Reader`s reads data models and returns relevant information, `Aggregator` combines and format the information, `Proposer` proposes a list of changes to be made in the data models, `Verifier` checks the proposed changes for correctness (or provide feedback that loops back to `Proposer`; this loop will run for a maximum of 3 times), and `Updater` updates the data models, finally `Notifier` replies to the user with the changes.
- Suggest a time for a new task
  - The assistant should suggest a time for a task based on the user's input. It either receives estimate of time needed or it estimates it directly, and it consults the schedule to find a suitable time slot.
  - Process: `Interpreter` identifies user request as this task, `Reader`s reads data models and returns relevant information, `Aggregator` combines and format the information, `Estimator` estimates or proposes a different estimate than the user provided time estimate, `Planner` finds a list of suitable time slots for inserting the task, and `Advisor` presents the information to the user.

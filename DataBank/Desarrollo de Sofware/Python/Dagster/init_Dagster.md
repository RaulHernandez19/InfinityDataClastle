```python
tester_monitoring_schedule = ScheduleDefinition(
    job=tester_monitoring_job,
    cron_schedule='0 * * * *'
)


updating_issues_board_schedule = ScheduleDefinition(
    job=updating_issues_board_job,
    cron_schedule='* * * * *'
)


defs = Definitions(
    jobs = [
        tester_monitoring_job                                
    ],

    schedules = [

        tester_monitoring_schedule,

        updating_issues_board_schedule

    ]

)
```
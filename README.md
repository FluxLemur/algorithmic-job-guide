# An Algorithmic Guide to Landing a Job
There are many guides that offer advice and tactics for how to get a job.

This guide is different. It offers advice in Python. No BS, no filler, purely
algorithmic. Note that [proper Pythonic
style](https://www.python.org/dev/peps/pep-0008/) is at times sacrificed for
readability.

Contributions are gladly welcomed!

```python
def get_job():
    """Gets you a job.

    The algorithm is broken into 5 basic steps:
    1. search
    2. apply
    3. interview
    4. evaluate offers
    5. accept
    """

    # search
    candidate_jobs = find_jobs()

    # apply
    update_your_info()  # resume, LinkedIn, website, etc.
    interviewing_at = set()
    for job in candidate_jobs:
        success = apply_for(job)
        if success:
            interviewing_at.add(job)

    # interview
    do_general_interview_prep()
    offers = set()
    for job in interviewing_at:
        prepare_for_interview(job)
        if interview_for(job):
            offers.add(job)

    # evaluate
    to_remove = set()
    for job in offers:
        is_acceptable = eval_offer(job):
        if not is_acceptable:
            to_remove.add(job)
    offers -= to_remove
    negotiate(offers)
    offers.sort(key=offer_evaluation_metric, reverse=True)

    # accept
    accept_offer(offers[0])  # !!
    for job in offers[1:]:
        reject_offer(job)
    celebrate()
```

## Search
```python
job_sources = [
    "recommendations from friends",
    "your College job board",
    "career fairs",
    "Google it",
    "LinkedIn",
    "Glassdoor",
    "Indeed",
    "Stack Overflow",
    "AngelList",
]

def find_jobs():
    jobs_found = []
    for source in job_sources:
        jobs_found.extend(find_jobs(source))
    # TODO you may want to prune jobs_found with some heuristic for whether
    # applying is worth your time/resources.
    return jobs_found
```

## Apply
```python
info_sources = [
    "resume",
    "LinkedIn profile",
    "personal website",
]

def update_your_info():
    for source in info_sources:
        update_info(source)

def apply_for(job):
    """Returns whether company decides to move forward with interviews."""
    move_forward = False
    if have_friend_at(job):
        move_forward = do_friend_referral(job)
    else:
        move_forward = send_application(job.apply_site)
        # also consider connecting with recruiters/employees at job on LinkedIn
    return move_forward
```

## Interview
```python
def do_general_interview_prep():
    # Google this
    # e.g. for software: Leetcode, HackerRank, Cracking the coding interview
    pass

def prepare_for_interview(job):
    research_company(job.company)
    prepare_questions_about(job)
    read_glassdoor_reviews(job)

def interview_for(job):
    """Interview for a job, and returns success status."""
    for stage in job.interview_stages:
        if not do_interview(stage):
            return False
    return True
```

## Evaluate
```python
def negotiate(offers):
    for offer in offers:
        notify_and_negotiate(offer.recruiting_contact, offers)

MAX_NUM_OFFER_AMENDMENTS = 3
def eval_offer(job):
    """Evaluates offer (possibly modifying it).

    Returns whether offer is acceptable.
    """
    read_offer(job)
    understand_offer(job)
    carefully_understand_offer(job)

    count = MAX_NUM_OFFER_AMENDMENTS
    while not offer_is_acceptable(job):
        if count <= 0:
            return False
        amend_offer(job)
        count -= 1
    return True

def offer_evaluation_metric(job):
    """Returns an integer representing your interest in your offer for `job`.

    Larger value implies greater interest.
    """
    # TODO this is generally personal, implement yourself!
    # As a very rough heuristic, use total compensation
    return job.total_compensation
```

## Accept
```python
def accept_offer(job):
    carefully_reread_offer(job)
    assert eval_offer(job)
    sign_offer(job)

def reject_offer(job):
    courteously_respond_to_your_recruiter(job)
```
- Note, an offer should be accepted before others are rejected.

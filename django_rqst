from django.http import HttpResponse
from django_rq import job, get_queue


@job
def trigger_event(**kwargs):
    return f"Hello, {kwargs['name']}!"


def trigger_event_view(request):
    event_data = {"name": "Awais", "age": 32}
    queue = get_queue()  # Get the default RQ queue
    job = trigger_event.delay(**event_data)
    response = f"Event triggered for {event_data['name']}, Age: {event_data['age']}"
    return HttpResponse(response)

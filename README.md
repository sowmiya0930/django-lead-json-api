# Django Lead Model – JSON API using Postman
## 1. Introduction
This project explains how to create a Lead model in Django and
retrieve the data in JSON format using Django REST Framework
and Postman.

## 2. Objectives
- To create a Lead model in Django
- To fetch Lead data in JSON format
- To test API using Postman

## 3. Technologies Used
- Python
- Django
- Django REST Framework
- Postman
- GitHub

## 4. Lead Model
`python``
from django.db import models
from django.contrib.auth.models import User

STATUS_CHOICES = [
    ('new', 'New'),
    ('working', 'Working'),
    ('qualified', 'Qualified'),
    ('disqualified', 'Disqualified'),
]

class Lead(models.Model):
    id = models.BigAutoField(primary_key=True)

    first_name = models.CharField(max_length=255)
    last_name = models.CharField(max_length=255, blank=True)
    email = models.EmailField(null=True, blank=True)
    phone = models.CharField(max_length=50, null=True, blank=True)

    company = models.CharField(max_length=255, blank=True)
    job_title = models.CharField(max_length=255, blank=True)

    lead_source = models.CharField(max_length=255, blank=True)
    status = models.CharField(max_length=50, choices=STATUS_CHOICES, default='new')

    owner = models.ForeignKey(User, on_delete=models.SET_NULL, null=True, related_name="leads")

    score = models.IntegerField(default=0)  # AI scoring future field

    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    notes = models.TextField(blank=True)
    ai_intent = models.CharField(max_length=255, null=True, blank=True)
    ai_notes_summary = models.TextField(blank=True)

    class Meta:
        ordering = ['-created_at']

    def __str__(self):
        return f"{self.first_name}{' ' + self.last_name if self.last_name else ''}"
 `python``

 ```md
 ```json

## output
[
{
    "id": 3,
    "first_name": "Sowmiya",
    "last_name": "G",
    "email": "sowmiya@example.com",
    "phone": "9876543210",
    "company": "ABC Tech",
    "job_title": "",
    "lead_source": "",
    "status": "new",
    "score": 0,
    "created_at": "2025-12-17T10:39:48.377986Z",
    "updated_at": "2025-12-17T10:39:48.378015Z",
    "notes": "",
    "ai_intent": null,
    "ai_notes_summary": "",
    "owner": null
}
]

```md
---
```md

## Conclusion
This project shows how to create a Lead model in Django and retrieve
data in JSON format using Postman. It helps in understanding basic
REST API development.





        
        





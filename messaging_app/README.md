# Building Robust APIs — messaging_app


## Overview
Develop a maintainable RESTful API using Django (optionally DRF) that implements messaging: users, conversations, and messages. Focus on correct models, relationships, routing, and best practices so the codebase is production-ready and easy to review.

## Objectives
- Scaffold a Django project and app.
- Implement User (extension of AbstractUser), Conversation, and Message models (UUID PKs).
- Define one-to-many and many-to-many relationships where appropriate.
- Build serializers that handle nested relationships (conversation with its messages).
- Implement viewsets (ConversationViewSet, MessageViewSet) and route them via DRF DefaultRouter.
- Follow project structure and security best practices.
- Validate and test endpoints locally (makemigrations, migrate, runserver).

## Repository & Paths
Repository: alx-backend-python  
Directory: messaging_app  
Main project: messaging_app/  
App: messaging_app/chats/  
Key files to create:
- messaging_app/README.md (this file)
- messaging_app/settings.py (add rest_framework, chats)
- messaging_app/chats/models.py
- messaging_app/chats/serializers.py
- messaging_app/chats/views.py
- messaging_app/chats/urls.py
- messaging_app/urls.py

## Quick Setup (commands)
- Create venv and install:
    - python -m venv venv
    - source venv/bin/activate
    - pip install django djangorestframework django-environ
- Scaffold:
    - django-admin startproject messaging_app .
    - python manage.py startapp chats
- Configure settings.py:
    - add 'rest_framework', 'chats' to INSTALLED_APPS
    - use django-environ or .env for secrets
- Migrate & run:
    - python manage.py makemigrations
    - python manage.py migrate
    - python manage.py runserver

## Models (high level)
- User (extends AbstractUser)
    - id: UUID primary key
    - first_name, last_name, email (unique), password_hash (handled by Django), phone_number, role (choices), created_at
- Conversation
    - id: UUID PK
    - participants: ManyToManyField(User, related_name='conversations')
    - created_at
- Message
    - id: UUID PK
    - conversation: ForeignKey(Conversation, related_name='messages', on_delete=CASCADE)
    - sender: ForeignKey(User, related_name='messages', on_delete=CASCADE)
    - message_body: TextField
    - sent_at: DateTimeField(auto_now_add=True)

Notes:
- Use models.UUIDField(default=uuid.uuid4, editable=False, primary_key=True)
- Enforce email unique and required fields
- Use related_name, on_delete, and indexes where appropriate

## Serializers
- UserSerializer
- MessageSerializer (include sender snapshot or id)
- ConversationSerializer
    - include nested messages (read-only or writable based on requirement)
    - include participants list (by id or nested user serializer)

## Views & Routing
- Implement ConversationViewSet and MessageViewSet using DRF viewsets.ModelViewSet or ReadOnlyModelViewSet + create endpoints
- Routes:
    - Use DefaultRouter and register:
        - router.register(r'conversations', ConversationViewSet)
        - router.register(r'messages', MessageViewSet)
    - Include router urls under project path: path('api/', include(chats.urls))

Example endpoint patterns:
- GET /api/conversations/
- POST /api/conversations/
- GET /api/messages/?conversation=<id>
- POST /api/messages/  (payload includes conversation and sender)

## Best Practices
- Use .env and django-environ for secrets; avoid hardcoding.
- Namespace routes and version APIs (e.g., /api/v1/).
- Keep business logic out of models; use managers or services.
- Commit migration files; test on a fresh DB.
- Add tests using Django test client; validate with Postman/Swagger.

## Project Assessment & Submission
To pass manual review:
- Complete tasks before deadline.
- Commit required files listed above.
- Generate your review link before the deadline.
- Request peers reviews and ask for Manual QA when done.

Auto-check: validates presence of core files for manual review.

Important: If the deadline passes you cannot generate a review link.

## How to request Manual QA
1. Ensure repository has all required files and migrations.
2. Push changes to the repo.
3. From the project dashboard, click "Request Manual QA" (or follow course platform instructions).
4. Include the review link and a short note about what was implemented.

---

Need additions or a condensed checklist for PR submission? Request it when ready for manual QA.
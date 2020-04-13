# Gibbon-mail

[![Docker Automated build](https://img.shields.io/docker/automated/stephaneklein/gibbon-mail)](https://hub.docker.com/r/stephaneklein/gibbon-mail)

Send mails with mjml Template  and JSON Schema.

- Project status: [POC](https://en.wikipedia.org/wiki/Proof_of_concept)
- Screencast: https://youtu.be/9oih7cZTjk4
- Docker Image: https://hub.docker.com/r/stephaneklein/gibbon-mail (Automated Builds configured on `master` branch)

To generate PDF instead send mails, see this project: [gibbon-pdf](https://github.com/stephane-klein/gibbon-pdf)

## Why this project?

- I would like to move transactionnal mail engine from my application in a separate service
- I would like to allow humans to send email manually, via a simple application plugged to the same API.
- I would like to keep a history (optionally) of all mail sent

## Quick start

Go to [`docker-image/`](docker-image/) and read the README.

or if you want to contribute see this READMEs:

- [`backend/`](backend/)
- [`frontend/`](frontend/)

## Roadmaps

- [x] Integrate [`mozilla-services/react-jsonschema-form`](https://github.com/mozilla-services/react-jsonschema-form)
- [x] Integrate [`mjmlio/mjml`](https://github.com/mjmlio/mjml)
- [x] Send mails with [nodemailer](https://nodemailer.com)
- [x] Add [mailhog](https://github.com/mailhog/MailHog) to test
- [x] Docker Image (`stephaneklein/gibbon-mail:latest`)
- [x] curl example
- [x] Screencast
- [x] Swagger
- [ ] Multi language mail template support #8
- [ ] Add [UISchema](https://react-jsonschema-form.readthedocs.io/en/latest/) support
- [ ] Check json input with JSON Schema
- [ ] Test frontend
- [ ] Configure CI
- [ ] Add option to save mail sent (in PostgreSQL)

[See other issues...](https://github.com/stephane-klein/gibbon-mail/issues)


## Features

- Send email from:
  - Json field values (validated by [JSON Schema](https://json-schema.org/))
  - [MJML](https://github.com/mjmlio/mjml) template file
  - TXT template file
  - Oneline Subject template file
- Rest API endpoints to generate mail preview or send email
- Web UI to generate email manually:
  - HTML form are autogenerated by [JSON Schema](https://json-schema.org/)
  - User can preview the email or send email
- Optionnaly record all email sent
- [cid](https://nodemailer.com/message/embedded-images/) image attachment support


## This project is based on this stack

- [Backend](backend/):
  - [NodeJS](https://nodejs.org/en/) with [Koa](https://koajs.com/)
  - [`mjmlio/mjml`](https://github.com/mjmlio/mjml) to generate Html email
  - [Nunjucks](https://mozilla.github.io/nunjucks/) to fill Email templates
  - [nodemailer](https://nodemailer.com) to send email
  - [Swagger](https://swagger.io/tools/swagger-ui/) (see [swagger.yaml](backend/src/swagger.yaml) file)
- [Frontend](frontend/)
  - [ReactJS](https://en.reactjs.org/), [Axios](https://github.com/axios/axios), [React-router](https://github.com/ReactTraining/react-router)
  - [react-jsonschema-form](https://github.com/mozilla-services/react-jsonschema-form) to generate Form from JSON Schema (need Bootstrap version `v3.3.6`)
  - [Bootstrap](https://getbootstrap.com/)
- Tooling
  - [Jest](https://jestjs.io/) and [supertest](https://github.com/visionmedia/supertest) for backend tests
  - [ESLint](https://eslint.org/)


## FAQ

### How can I enable Authentication system?

This project hasn't build-in authentication system, it's a internal service in your stack,
you must protect it by a private network or [Basic access authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) system.

### Why « Gibbon-mail » name?

[Gibbon](https://en.wikipedia.org/wiki/Gibbon) as an allusion to [Mandrill App](https://mandrill.com/).


---

Emails examples:

- [Sentry](https://github.com/getsentry/sentry/tree/master/src/sentry/templates/sentry/emails)
- [GitLab](https://gitlab.com/gitlab-org/gitlab-ce/tree/master/app/views/notify)

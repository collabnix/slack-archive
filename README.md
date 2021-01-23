# collabnix/slack-archive

Archiving Slack conversations for Collabnix Community

## Story

On a fine day early this week, [`@dostiharise`](https://github.com/dostiharise) logged into Collabnix's `#golang` Slack channel to discuss thoughts on upcoming `go 1.16` release and experimental `darwin/arm64` support for Apple Silicon M1 chip.

<br>

> [@dostiharise](https://github.com/dostiharise) 2:17 PM
>
> All our conversations are gone.😳<br>
> Should have archived them.
>
> Any ideas on how to not loose the conversations?<br>
> We could run a scheduled archiver and have them indexed on s3 or something.

> [@ajeetraina](https://github.com/ajeetraina) 2:20 PM
>
> GitHub is a new search engine for Developers 🙂

> [@dostiharise](https://github.com/dostiharise)  2:20 PM
>
> Oh, yeah thats a good idea.
> Commit to Github.

> [@ajeetraina](https://github.com/ajeetraina) 2:21 PM 
> 🙂

> [@dostiharise](https://github.com/dostiharise) 2:21 PM
>
> Nice, let me see what we can do.

> [@dostiharise](https://github.com/dostiharise) 2:29 PM
>
> By the way, can we setup a repo under collabnix that says [“slack-archive”](https://github.com/collabnix/slack-archive) please?
>
> Let’s drive this project. May be it can help many other Slack communities out there. 🤞

> [@ajeetraina](https://github.com/ajeetraina) 2:31 PM
>
> Sure!<br>
> I have created a new repo: [collabnix/slack-archive](https://github.com/collabnix/slack-archive).
>

> [@dostiharise](https://github.com/dostiharise) 2:21 PM
>
> I got the invite, thanks a ton. 👍



<br>

And here we are!

## Overview

Collabnix community uses a free version of Slack to communicate which has a limit of 10,000 slack messages, beyond which we start losing old conversations. We hit this limit of 10,000 messages a long time ago, and because of this, valuable conversations were lost. Since we are growing fast this problem will only amplify over time.

Our intention behind this project is to preserve these conversations in a long-term archive, as they can prove to be valuable for its members and the rest of the developer community at large.

## Design (Draft)

To acquire the Slack messages and archive them we will need the following steps:

0. Slack Authentication (User/Bot)
1. Slack Message Ingestion (Batch/Stream)
2. Slack Message Encoder (JSON/Markdown/AsciiDoc)
3. Slack Message Storage (S3/GS/PostgreSQL/RocksDB)

To make the archive useful we may need to add some search and discovery on top of the storage layer.

4. Slack Message Indexing (DynamoDB/DataStore/BigTable/Athena/ElasticSearch/Loki)
5. Slack Message Querying (ReactJS/Kibana/Grafana/cURL)

> An interesting idea from [@ajeetraina](https://github.com/ajeetraina) (Ajeet Singh Raina) was to use Github as our storage layer so that we get the Search (Indexing and Querying) for free. 😋

## Stack 

I am proposing the following technologies to begin with. Suggestions are welcome.

Web Client:

- HTML5, CSS3
- JavaScript
- ReactJS

Web Server:

- go
- gorilla/mux

Cloud Services:

- Slack
- AWS S3
- AWS CloudWatch Events (Batch Mode)
- AWS Lambda (Batch Mode)
- AWS ECS/EKS (Stream Mode)

## Privacy

We will need to take extra care before we store any Slack messages in the public domain. We plan on starting with the job board channels (`#jobs` and `#devops-job-seeker`) from our [Collabnix's Slack](collabnix.slack.com) since the messages posted on these channels are expected to be public.

## Contributors

- [Hari Krishna Ganji](https://www.linkedin.com/in/harikrishnaganji) ([@dostiharise](https://github.com/dostiharise))
- [Ajeet Singh Raina](https://www.linkedin.com/in/ajeetsraina) ([@ajeetraina](https://github.com/ajeetraina))
- Join us. Go ahead, submit your pull request already! 👩‍💻🙂

## Sponsorship

- [Alvyl Consulting](alvyl.com) ([@alvyl](https://github.com/alvyl)) will be sponsoring AWS cloud hosting for this project.

## Reach us

If you would like to contribute Ideas, Design, Code, Tests, or Hosting for this project, please reach out to [@dostiharise](https://github.com/dostiharise) or [@ajeetraina](https://github.com/ajeetraina) at [Collabnix's Slack](collabnix.slack.com). 

We would love for other Slack communities out there to participate and benefit from this project. Feel free to reach out to us on [Collabnix's Slack](collabnix.slack.com).

<br>

Have a nice day! 🏖
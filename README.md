# pocketcasts-readme
Updates README with recently listened podcasts from Pocketcasts

# Setup

## Prep Work

1. You need to save the pocketcasts Email & Password in the repository secrets. You can find that in the Settings of your Repository. Be sure to save those as the following.

    - `POCKETCASTS_EMAIL = <your  Pocketcasts Email>`
    - `POCKETCASTS_PASSWORD = <your  Pocketcasts Password>`

# Update your README

Add a comment to your README.md like this:

```markdown
# # Recently Listened Podcasts

<!-- PODCAST-LIST:START -->
Lex Fridman Podcast: [#360 – Tim Urban: Tribalism, Marxism, Liberalism, Social Justice, and Politics](https://media.blubrry.com/takeituneasy/content.blubrry.com/takeituneasy/lex_ai_tim_urban_2.mp3)

Finshots Daily: [Do we need a Global Biofuel Alliance?](https://anchor.fm/s/37a76020/podcast/play/76032122/https%3A%2F%2Fd3ctxlq1ktw2nl.cloudfront.net%2Fstaging%2F2023-8-18%2F68b356ff-04b8-2eb2-2f8f-31ea09d827a1.mp3)

The Knowledge Project with Shane Parrish: [#127 Best of 2021: Conversations of the Year](https://traffic.libsyn.com/secure/theknowledgeproject/Episode_127_-_Best_of_2021.mp3?dest-id=271299)

The Changelog: Software Development, Open Source: [OpenTF sticks a fork in Terraform](https://op3.dev/e/https://cdn.changelog.com/uploads/news/59/changelog-news-59.mp3)

The Knowledge Project with Shane Parrish: [#167 Dr. Gina Poe: The Science of Better Sleep](https://traffic.libsyn.com/secure/theknowledgeproject/167_Gina_Poe.mp3?dest-id=271299)


<!-- PODCAST-LIST:END -->
```

# Repository Workflow

Please follow the steps below:

1. Go to your `<username>/<username>/actions`, hit New workflow, set up a workflow yourself, delete all the default content github made for you.
2. Copy the below code and paste it to your new workflow


```
name: Update pods
on:
    workflow_dispatch:
    schedule:
    # Runs every 8 hours
    - cron: "0 */8 * * *"

permissions:
    contents: write

jobs:
    build:
        runs-on: ubuntu-latest

        steps:
            - name: Checkout Code
              uses: actions/checkout@v3
            - name: Update README
              uses: maheshrjl/pocketcasts-readme@main
              with:
                  POCKETCASTS_EMAIL: ${{ secrets.POCKETCASTS_EMAIL }}
                  POCKETCASTS_PASSWORD: ${{ secrets.POCKETCASTS_PASSWORD }}
            - name: Push Changes
              uses: stefanzweifel/git-auto-commit-action@v4
```


## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Mahesh Rijal](https://maheshrjl.com/) has waived all copyright and related or neighboring rights to this work.

_Inspired by [abhisheknaiidu/todoist-readme](https://github.com/abhisheknaiidu/todoist-readme)_

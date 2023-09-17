# P!MOLA

Meet your next media librarian, p!MOLA!

p!MOLA stands for _parallelized Media Organizer, Library manager, Archiver_.

Project will be mainly written in **javascript**, i will use `nodejs` but will also try to add `bun` overloads where it's useful (for example, writing files, idk)

## Features

> Keep in mind this project is BARELY STARTED (last update 17th of september, 2023) so don't expect a working or user-friendly project YET.
> Follow the organization and the core repo and get updated for new feature promises and implemented features!

My personal wishlist:

- [ ] Archival:
  
  - [ ] Organize playlists and medias in library metadata files, working in a similar manner to `package-lock.json` but in YAML
  - [ ] Use disk cache AND `tmpfs` storage for operations where it makes sense. (Haven't figured out any temporary file system solutions for Windows yet.)
  - [ ] Use `youtube-dl` (also allowing drop-in replacements like `yt-dlp`) to get content

- [ ] Library Management:
  
  - [ ] Using multiple players? Create compatible separate library folders or just use the most common features and have a common library!
    No more flac files mixed with mp3 files!

  - [ ] Share libraries or library recipes (from now on called medialists) with other users or sync changes you made in your own machine to your media console!

- [ ] Media Organizing:
  
  - [ ] Episodes!
    If the media you get has episodes (for example, with CUE sheets), p!MOLA can prepare it for your favorite player!
    (Depending on your preferences and preferred player, p!MOLA might split the files into an album folder, strip/embed the episode information or just leave it as is.)
  - [ ] Force use

- [ ] Parallelization:
  (say goodbye to your free CPU time /s)

  - [ ] Pre-fetch all playlist and media id's to optimize future tasks
  - [ ] Implement a queue system to manage tasks

- [ ] Automation:
  
  - [ ] Project Automation:
    (yes, "AI"s we wrote will take our maintainer(s) non-paid jobs, how sad)
    - [ ]
  - [ ] Library/Archive Automation

- [ ] Optimizations:
  
  - [ ] Media Player Optimizations
  - [ ] P-MOLA Optimizations
    - [ ] Use a cache folder to cache and re-use **downloaded** files
    - [ ] Use a tmpfs system (like `/tmp/`)

- [ ] Interfaces! (No, the clicky ones!)
  
  - [ ] Provide web API for basic operations like
    - [ ] Adding media to library
      - [ ] via upload
      - [ ] via youtube-dl line (not final)
      - [ ] via p-mola medialist files/archives (why not)
    - [ ] Streaming music to device/player
    - [ ] Configuring preferences
      - [ ] Streaming settings
      - [ ] Player preferences
      - [ ] Media library locations
      - [ ] Cache management
    - [ ] Seeing live progress of media downloading

- Make the library management files work in yaml and possibly document db modes, to either ease the migrations to another server or to optimize the self organizing.

---

Those were CORE features, only backends.

- I also plan to provide local-first web APIs to allow user-friendly web/native interfaces to be made.
- Allow automation? How? dunno.
  Might involve webhooks and scripts at some point.

## Player Metadata API

Schema is not defined yet but this project should allow you to supply a semver version string and the player identifier (for example, `AIMP:mobile`) to make your library as compatible with your app as possible.

However I would love to achieve at least these:

- [ ] Core
  - [ ] Schema definition
  - [ ] Making test scenarios
- [ ] Future goals
  - [ ] Allow player developers themselves add their information
    - [ ] Implement a bot that will
      - [ ] Make sure the developer changed only their allowlisted files
      - [ ] Make sure it is the developer who sent the change (might look into private signing submissions or verifying via GPG keys)
      - [ ] Submit a PR with new info
      - [ ] Review submitted PRs
        - [ ] Make sure the new file is still compliant with the schema
        - [ ] Make sure the new file is symlinked as `latest.yaml`, or warn and ask the developer to proceed
          This could be useful on situtations where a developer wanted to upload beta information, for example.
      - [ ] When given green flag, auto merge the PR.

  Not tied to the p!MOLA project itself but
  - [ ] Create periodic graphs/tables for player compatibility

# yutu

GitHub action for YouTube, powered by [yutu🐰](https://github.com/eat-pray-ai/yutu).

## Example

See [youtube-uploader](https://github.com/eat-pray-ai/youtube-uploader) for an detailed example.

```yaml
- uses: eat-pray-ai/yutu/actions/general@main
  with:
    version: 0.9.5
    credential: ${{ secrets.YOUTUBE_CREDENTIAL }}
    token: ${{ secrets.YOUTUBE_TOKEN }}
    command: video
    subcommand: insert
    flags: '-f ${{ inputs.file }} -t ${{ inputs.title }} ${{ inputs.rest-flags }}'
```

## Inputs

### `version`

**Optional**, The version of yutu to use, `v0.8.2` for example, leave empty to use the latest version.

### `credential`

**Required**, Please refer to [yutu prerequisites](https://github.com/eat-pray-ai/yutu?tab=readme-ov-file#prerequisites) to get a credential.

Note: The credential should be base64 encoded as input, for example:

```shell
base64 -w 0 client_secret.json
```

### `token`

**Required**, Please refer to [yutu prerequisites](https://github.com/eat-pray-ai/yutu?tab=readme-ov-file#prerequisites) to generate a token.

Note: The token should be base64 encoded as input, for example:

```shell
base64 -w 0 youtube.token.json
```

### `command`

**Optional**, The command to run, for all available commands:

```shell
❯ yutu --help
yutu is a fully functional CLI for YouTube, which can be used to manupulate YouTube videos, playlists, channels, etc.

Usage:
  yutu [flags]
  yutu [command]

Available Commands:
  activity               List YouTube activities
  auth                   Authenticate with YouTube API
  caption                Manipulate YouTube captions
  channel                Manipulate YouTube channels
  channelBanner          Insert Youtube channelBanner
  channelSection         Manipulate channel section
  comment                Manipulate YouTube comments
  commentThread          Manipulate YouTube comment threads
  completion             Generate the autocompletion script for the specified shell
  help                   Help about any command
  i18nLanguage           List YouTube i18nLanguages
  i18nRegion             List YouTube i18nRegions
  member                 List YouTube members
  membershipsLevel       List YouTube memberships levels
  playlist               Manipulate YouTube playlists
  playlistItem           Manipulate YouTube playlist items
  search                 Search for Youtube resources
  subscription           Manipulate YouTube subscriptions
  thumbnail              Set thumbnail for a video
  version                Show the version of yutu
  video                  Manipulate YouTube videos
  videoAbuseReportReason List YouTube video abuse report reasons
  videoCategory          List YouTube video categories
  watermark              Manipulate Youtube watermarks

Flags:
  -h, --help   help for yutu

Use "yutu [command] --help" for more information about a command.
```

### `subcommand`

**Optional**, The subcommand corresponding to the command, to get all available subcommands for a command:

```shell
❯ yutu <command> --help
❯ yutu playlist --help
Manipulate YouTube playlists, such as insert, update, etc.

Usage:
  yutu playlist [flags]
  yutu playlist [command]

Available Commands:
  delete      Delete a playlist
  insert      Create a new playlist
  list        List playlist's info
  update      Update an existing playlist

Flags:
  -h, --help   help for playlist

Use "yutu playlist [command] --help" for more information about a command.
```

### `flags`

**Optional**, Flags passed to yutu, to get all available flags for a command and subcommand:

```shell
❯ yutu <command> <subcommand> -h
❯ yutu subscription insert --help
Insert a subscription

Usage:
  yutu subscription insert [flags]

Flags:
  -c, --channelId string             ID of the channel to be subscribed
  -d, --description string           Description of the subscription
  -h, --help                         help for insert
  -s, --subscriberChannelId string   Subscriber's channel ID
  -t, --title string                 Title of the subscription
```


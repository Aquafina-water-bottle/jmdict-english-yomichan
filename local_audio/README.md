
# Local Audio Server for Yomichan

This is a completely optional setup for people who want to be
able to create Anki cards nearly instanteously, and without
a working internet connection.

> **Note**
>
> This is an updated version of
> [TMW's guide](https://learnjapanese.moe/yomichan/#offline-audio-server).
> Much of the info was taken from the above link.


> **Warning**
>
> I did NOT make these plugins, and cannot provide detailed support for when things go wrong.
> Credits are given in the respective folders.



<details>
<summary>Advantages and Disadvantages of using this setup <i>(click here)</i></summary>


* **Advantages:**

    1. Most audio is gotten in **less than a second**. Without the local audio server,
        fetching the audio can take anywhere from three seconds to a full minute
        (on particularily bad days).

        Most of the delay from Yomichan when creating cards is from fetching the audio.
        In other words, getting the audio is the main bottleneck of when creating Anki cards.
        This setup removes this bottleneck, and allows you to make cards **nearly instaneously**.

    1. If you do not have internet access, you can still add audio to your cards.

* **Disadvantages:**

    1. This setup requires a little over **3GB of free space**.

    1. This setup is only available for PC. Although there have been talks to port this to Android,
        this is not currently feasable because most users do not want to waste
        3GB of space on their phone.

        Of course, if you're interested in porting this to work with Android, you are always free
        to contribute to [AnkiConnectAndroid](https://github.com/KamWithK/AnkiconnectAndroid)!

    1. It only has the coverage of jpod and nhk16
        (which is still about 99% coverage, from personal experence).
        To increase audio coverage,
        it would be ideal to also include an extra
        [Forvo audio source](https://learnjapanese.moe/yomichan/#bonus-adding-forvo-extra-audio-source).

</details>


## Steps

1.  There are two main versions of the add-on. Download one of the two.

    - **Option 1**: [SQL-based](https://github.com/Aquafina-water-bottle/jmdict-english-yomichan/blob/master/local_audio/sql/localaudio_2022_06_09_sqlite.ankiaddon?raw=true) (highly recommended)
    - **Option 2**: [Memory-based](https://github.com/Aquafina-water-bottle/jmdict-english-yomichan/blob/master/local_audio/07/localaudio_v07.ankiaddon?raw=true)

    If you are interested, here are the differences between the two versions:

    <details> <summary>Comparing Memory-based VS SQL-based versions <i>(click here)</i></summary>

    The SQL-based version stores the map in a local database file on your computer.
    This version queries this database when fetching the audio.

    The memory-based version generates and caches the map in memory.
    This is the original version of the add-on.
    The SQL-based version is a patch on-top of this version.

    Advantages and disadvantages of each version:

    - The SQL database only has to be generated once, as this database is
        stored on the disk.

        The memory-based version must regenerated its cache
        **every time you re-open Anki**.
        This indeed has noticable effects;
        the cache is only regenerated when audio is fetched,
        so the first card added after every Anki restart will take noticably longer than normal.

    - The memory-based version hogs about ~250MB of memory,
        which is a problem on slow computers.
        The SQL-based version does not hog memory.

    - The memory-based version is slightly faster than the SQL-based version.

    </details>

1. Install the add-on by heading over to:

    > (Anki) →  `Tools` →  `Add-ons` →  `Install from file...`

1. Download all the required audio files.
    They can be found at this [torrent link](https://nyaa.si/view/1544279).

    <details> <summary>Magnet link <i>(click here)</i></summary>

        magnet:?xt=urn:btih:71a2b5107e90f69e0c4cb19187d6a1e2f7b3404f&dn=local_audio.7z&tr=http%3a%2f%2fanidex.moe%3a6969%2fannounce&tr=http%3a%2f%2fnyaa.tracker.wf%3a7777%2fannounce&tr=udp%3a%2f%2ftracker.coppersurfer.tk%3a6969%2fannounce&tr=udp%3a%2f%2fexodus.desync.com%3a6969%2fannounce&tr=udp%3a%2f%2ftracker.opentrackr.org%3a1337%2fannounce&tr=udp%3a%2f%2fopen.stealth.si%3a80%2fannounce&tr=udp%3a%2f%2ftracker.leechers-paradise.org%3a6969%2fannounce&tr=udp%3a%2f%2ftracker.tiny-vps.com%3a6969%2fannounce&tr=udp%3a%2f%2ftracker.torrent.eu.org%3a451&tr=udp%3a%2f%2ftracker.moeking.me%3a6969%2fannounce

    </details>

1. Place the audio files under `Anki2/addons21/955441350/user_files`.
    See [Anki's documentation](https://docs.ankiweb.net/files.html#file-locations)
    on instructions to find your `Anki2` folder.

    <details> <summary>Expected file structure <i>(click here)</i></summary>

        user_files
        ├── jpod_alternate_files
        │   └── よむ - 読む.mp3
        │   └── ...
        ├── jpod_files
        │   └── よむ - 読む.mp3
        │   └── ...
        └── nhk16_files
            ├── audio
            │   └── 20170616125910.aac
            │   └── ...
            └── entries.json

    </summary>

1. In Yomichan Settings, go to:

    > `Audio` →  `Configure audio playback sources`.

    Click `Add`, and set the source to be `Add Custom URL (JSON)`.

    Set the `URL` field to:
    ```
    http://localhost:5050/?sources=jpod,jpod_alternate,nhk16&term={term}&reading={reading}
    ```

    The sources can be rearranged to give priority to a different source
    For example, if you want nhk16 to have the highest priority, use `sources=nhk16,jpod,jpod_alternate`.

1. (If you are using the SQL-based version)

    Generate the SQL database by scanning any word (e.g. 読む),
    and then play the audio.

    Expect this to take a while.


## Original Message

<sup>
<a href="https://discord.com/channels/617136488840429598/778430038159655012/943743205931900928">Original discord message</a>, on
<a href="https://learnjapanese.moe/join/">TMW server</a>
</sup>


Zetta — 16/02/2022 <br>
Yomichan Local Audio Server Anki Plugin V0.1 (probably buggy) This plugin acts similar to the Forvo Audio Server plugin but runs off the downloaded JapanesePod audio files. The purpose is to provide offline access and faster look ups for audio that exists in the dump.

Any audio files with the format of `<reading> - <term>.mp3` under the plugins `user_files` directory will be used. Folder structure under `user_files` doesn’t matter. For example `よむ - 読む.mp3` it will try to match the yomichan entry to both reading and term and show up as `Local (Exact)` Failing that, it will just use `reading` and show up as `Local (Reading)` in the yomichan audio dropdown.

How to use:

1. Install the attached addon like any other local addon.
1. Restart Anki
1. Allow network connections (required since this is a local server)
1. In yomichan settings, go to Audio > Configure Audio Playback Sources > Custom Audio Source
1. Select Type as JSON and set URL to `http://localhost:5050/?term={term}&reading={reading}`
1. Download the JapansePod Audio dump from here https://discord.com/channels/617136488840429598/778430038159655012/943679275884740608 and unzip all archives it in your Anki2 folder under `addons21/955441350/user_files`
1. (You may need to Restart Anki again if it doesn’t start working.)

Bugfix for multiple files named the same in different directories under user_files. https://discord.com/channels/617136488840429598/778430038159655012/943876430746513429 <br>
Credit: Much of the code was ripped from https://github.com/jamesnicolas/yomichan-forvo-server



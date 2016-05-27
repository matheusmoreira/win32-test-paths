# win32-test-paths

Test repository with paths that have characters reserved by Windows.

---

A couple months ago [I tweeted to GitHub Support][tweet] about an issue in GitHub Desktop involving special characters in file names:

![Files with `?` in their names would show up as deleted][tweet-image]

So I created this test repository to reproduce the issue and document the behavior.

I managed to reproduce it using Git Shell:

![Results of `git status` running on GitHub's Git Shell][github.git-status]

Meanwhile, when running on top of my standalone `msys2` installation's shell, `git` can deal with the files just fine:

![Results of `git status` running on my own msys2 shell][msys2.git-status]

NTFS clearly supports these characters. Prepending a `\\?\` to paths in order to force them to be passed as-is to the file system driver seems like a possible fix to this issue.

[tweet]: https://twitter.com/mammoreira/status/725855931272183808
[tweet-image]: screenshots/github-for-windows/github-desktop/tweet-mammoreira:725855931272183808.jpg
[github.git-status]: screenshots/github-for-windows/git-shell/git%20status.png
[msys2.git-status]: screenshots/msys2/git%20status.png

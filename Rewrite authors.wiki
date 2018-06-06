Rename commit authors:
--------------------------------------------------
    git filter-branch --env-filter '
        if [ "$GIT_COMMITTER_EMAIL" = "user@1db3dd96-1627-47d4-83f9-2d82c1e3f9e7" ]; then
            export GIT_COMMITTER_NAME="User Name"
            export GIT_COMMITTER_EMAIL="u.name@keepthinking.it"
        fi
        if [ "$GIT_AUTHOR_EMAIL" = "user@1db3dd96-1627-47d4-83f9-2d82c1e3f9e7" ]; then
            export GIT_AUTHOR_NAME="User Name"
            export GIT_AUTHOR_EMAIL="u.name@keepthinking.it"
        fi
    ' --tag-name-filter cat -f -- --all
--------------------------------------------------



Check it:
--------------------------------------------------
    git log | grep "Author" | sort -u
--------------------------------------------------

Push it back to repo
--------------------------------------------------
    git push --force --tags origin 'refs/heads/*'
--------------------------------------------------





And then, in other local repo's update rewritten history:
--------------------------------------------------
    git fetch
    git reset --hard origin/master
--------------------------------------------------

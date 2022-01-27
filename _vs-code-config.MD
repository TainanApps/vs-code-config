# VS Code Configuration

## Recommended Extensions

- Live Server
- Dracula Official
- Prettier
- Material Icon Theme
- ES7+ React/Redux/React-Native snippets
- Git Lens
- Reactjs code snippets

## Settings (ctrl+,)

- User settings, set the default to Prettier
  ![default-formatter](https://user-images.githubusercontent.com/98510717/151345509-c59d18ba-2034-4857-9f0c-58f48043c555.png)

- User settings, set the format to on paste and save to on
  ![format-on-save](https://user-images.githubusercontent.com/98510717/151345843-d44697d0-01e8-4eeb-8274-49cf965b929f.png)

- In the user JSON settings enter the following

  ![emmet-json](https://user-images.githubusercontent.com/98510717/151345770-4d466c48-acc5-42c3-a639-350bc749add7.png)

## Set Gitbash as default terminal profile

> Shift+Ctrl+P (or Shift+Cmd+P) and then type in

```
> Select default terminal
```

> Choose the Git Bash terminal profile

## Configure Gitbash git-prompt.sh file

- Windows: c:/program files/git/etc/profile.d/git-prompt.sh

```shell
parse_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}

if test -f /etc/profile.d/git-sdk.sh
then
	TITLEPREFIX=SDK-${MSYSTEM#MINGW}
else
	TITLEPREFIX=$MSYSTEM
fi

if test -f ~/.config/git/git-prompt.sh
then
	. ~/.config/git/git-prompt.sh
else
	PS1='\[\033]0;$TITLEPREFIX:$PWD\007\]' # set window title
	PS1="$PS1"'\n'                 # new line
	PS1="$PS1"'\[\033[32m\]'       # change to cyan
	PS1="$PS1"'`parse_git_branch`'' \[\033[33m\]'    # bash function
	PS1="$PS1"'\W'                 # current working directory
	if test -z "$WINELOADERNOEXEC"
	then
		GIT_EXEC_PATH="$(git --exec-path 2>/dev/null)"
		COMPLETION_PATH="${GIT_EXEC_PATH%/libexec/git-core}"
		COMPLETION_PATH="${COMPLETION_PATH%/lib/git-core}"
		COMPLETION_PATH="$COMPLETION_PATH/share/git/completion"
		if test -f "$COMPLETION_PATH/git-prompt.sh"
		then
			. "$COMPLETION_PATH/git-completion.bash"
			. "$COMPLETION_PATH/git-prompt.sh"
			PS1="$PS1"'\[\033[33m\]'  # brownish yellow
		fi
	fi
	PS1="$PS1"'\[\033[0m\]'        # change color
fi

MSYS2_PS1="$PS1"               # for detection by MSYS2 SDK's bash.basrc

# Evaluate all user-specific Bash completion scripts (if any)
if test -z "$WINELOADERNOEXEC"
then
	for c in "$HOME"/bash_completion.d/*.bash
	do
		# Handle absence of any scripts (or the folder) gracefully
		test ! -f "$c" ||
		. "$c"
	done
fi
```

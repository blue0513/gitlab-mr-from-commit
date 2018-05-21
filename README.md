# GitLab-MR-From-Commit

Open MR page in GitLab associated with a Commit.  
It works Not Only in Terminal but also Editor like Emacs!!

This Project is fully respecting [This Project](http://blog.shibayu36.org/entry/2018/05/08/193000).

[terminal](./images/terminal.gif)

[emacs](./images/emacs.gif)

## Quick Start on Terminal

#### 1. Fill the variables in `gitlab-mr-from-commit`

```sh
# Get it from gitlab
# See: https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html
PRIVATE_TOKEN='[YOUR PRIVATE TOKEN]'

# Get it from your project's setting page
# On the Edit Project page in GitLab, there is a Project ID field in the top right corner.
PROJECT_ID='[YOUR PROJECT ID]'

# It should be like `https://gitlab.com`
PROJECT_BASE_URL='[YOUR PROJECT BASE URL]'

# Directory should be `my-project/product1`
PROJECT_DIRECTORY='[YOUR PROJECT DIRECTORY]'
```

#### 2. Set the PATH

```sh
# In your .bashrc or .zshrc or so
# Set the PATH as bellow
export PATH="$HOME/gitlab-mr-from-commit:$PATH"
```

#### 3. Execute!!

```sh
# It will open MR on GitLab!
$ gitlab-mr-from-commit [YOUR_COMMIT_HASH]
```

### Using with [Tig](https://github.com/jonas/tig)

#### 1. Install tig

```sh
$ brew intall tig
```

#### 2. Execute with tig!!

```sh
# Open tig
$ tig [FILE]

# Then Type...
$ Shift+o

# That's All
```

## Start on Emacs

#### 1. Add a function on your nice `init.el` (quoted from [Here](http://blog.shibayu36.org/entry/2018/05/08/193000))

```elisp
;; init.el
(defun gitlab-open-mr ()
  (interactive)
  (let* ((rev-at-line (vc-annotate-extract-revision-at-line))
		 (rev (car rev-at-line)))
	(shell-command (concat "gitlab-mr-from-commit " rev))))

;; key bind
(global-set-key (kbd "C-o") 'gitlab-open-mr)
```

#### 2. Execute with `vc-annotate`!!

```elisp
;; In a file, under the Git Control....
M-x vc-annotate RET Ctrl+o

;; That's All
```

# slyle-guidelines


## Setting a Custom Git Commit Message Template
To set a custom Git commit message template for your repository, follow these steps:

1. Download the *git_commit_template.txt* file.

2. Open your terminal or command prompt and navigate to your Git repository.

3. Set the *commit.template* configuration option to the path of your custom template file by using the following command:

<pre>
&emsp;git config --global commit.template git_commit_template.txt
</pre>

Note that the *--global* option sets the configuration globally for all Git repositories on your machine. If you only want to set the configuration for the current repository, you can omit the *--global* option.

The next time you create a commit, Git will use your custom template as the default commit message. You can still modify the message as needed before finalizing the commit.

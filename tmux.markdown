Tmux
----

My "ide" is generally just vim and tmux. If I'm working on a rails project,
one screen is devoted to vim, running tests, source control, etc. Another runs
the development server. Perhaps a third sits in the Rails source to quickly
look up methods and documentation.

#### Sesssions

    tmux new -s <name>    --> Creates a tmux session named <name>
    <C-B> D               --> Leave the current session.
    tmux a -t <name>      --> Attach to the session named (or beginning with name) <name>

#### Windows

    <C-B> C               --> Create a new window.
    <C-B> <num>           --> Open window <num>
    <C-B> N/P             --> Open next/previous window
    <C-B> L               --> Open last window
    <C-B> , <name>        --> Name the current window (e.g., "Server")

#### send-keys

    $ tmux send-keys -t 1 'ruby -Itest test/models/user_test.rb' C-m     --> Run the command on window 1

With Vim:

    :map ,t :w\|!tmux send-keys -t 1 'ruby -Itest %' C-m <cr>

(The `C-m` is to run the command on the target shell; the `<cr>` is to run the Vim command.)

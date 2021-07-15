This simple terminal program was made to assist with properly identifying issues with plugins in a clean environment, without having to touch your config.

Edit `test_plugin` to configure where the testing template is and 
`chmod` it. 
Add it to your `$PATH` if you want.

Pass the names of the plugins you want to test:

`test_plugin tpope/vim-surround tpope tpope/vim-repeat`

At each invocation `test_plugin.vim` is cleaned up with `git checkout HEAD -- $TEST_FILE`.
So if you want to add some options or mappings ot it you can't live without commit them.


## zsh completion

Add the following script name `test_plugin`
    
    #compdef test_plugin
    
    PLUGINS=$(awk -F\' '$1 ~ /Plug/ {print $2}' $PLUGINS_FILE
    
    _alternative "plugins:plugins:($PLUGINS)"


in your correscponding `Completion/Linux` directory, for example
`/usr/share/zsh/functions/Completion/Linux/`

Replace `$PLUGINS_FILE` with the absolute path to the file where your
plugs are defined.

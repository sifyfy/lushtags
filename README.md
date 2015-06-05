lushtags
========

This repository is forked from
(bitc/lushtags)[https://github.com/bitc/lushtags] because it was not
maintained (at least it looked so to me). The difference from the last
fork is shown in the last section.

Create ctags compatible tags files for Haskell programs

Similar programs are [hasktags][1], [gasbag][2], [hothasktags][3], and GHC's
builtin ctags generation.

lushtags differs from these by being designed to have smooth integration with
the [Vim Tagbar][4] plugin.

Tagbar is nice because it deals with creating tags automatically. There is no
need to manually run commands or keep track of tag files. Just open any Haskell
file in Vim and the Tagbar window will instantly show an interactive browsable
list of all the functions and declarations in the file. This window also
updates automatically as you edit the file.

The tags created by lushtags are marked with several extensions, so that when
used with Tagbar you get these features:

- Type signatures are displayed for functions.
- Tags are properly scoped so that, for example, data declarations appear as a
  tree with their constructors scoped as children.
- Definitions that are exported from the module are marked as "public" and
  appear emphasized in Tagbar.
- Tag locations are internally stored as patterns, not line numbers, so that
  you can correctly jump to tags even if they have moved in the source code
  during editing.

![screenshot](https://github.com/bitc/lushtags/raw/master/doc/screenshot-tagbar-2011-09-19.png)

The original version of lushtags could not handle fields, but this
version can handle them.

![screenshot2](https://www.evernote.com/shard/s75/sh/4f23351b-d866-4069-8de2-a44fd48faa53/077f4a3afd974cda/res/ec3327c2-1961-4aec-985e-ef9661530b93/skitch.png)

[1]: http://hackage.haskell.org/package/hasktags
[2]: http://kingfisher.nfshost.com/sw/gasbag/
[3]: http://hackage.haskell.org/package/hothasktags
[4]: http://majutsushi.github.com/tagbar/

Using lushtags with Vim and the Tagbar plugin
---------------------------------------------

1. Build and install the lushtags executable

        $ cabal configure
        $ cabal build
        $ cabal install

2. Install the Tagbar plugin. Tagbar can be found at

    <http://www.vim.org/scripts/script.php?script_id=3465>
    <http://majutsushi.github.com/tagbar/>

3. Install the included Haskell Tagbar configuration:

        $ cp plugin/tagbar-haskell.vim ~/.vim/plugin/

4. Try it out:

        $ vim Hello.hs

Now open the Tagbar with the command `:TagbarOpen`. An interactive sidebar will
appear with all of the tags in your Haskell source file.

Differences from bitc/lushtags
------------------------------

- Complatible with GHC 7.8.4 (probably with 7.8.3 as well)
- Outputs record functions.

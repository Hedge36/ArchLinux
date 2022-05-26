# Keybindings

| Movement              |                                                              | Mapping name                        |
| --------------------- | ------------------------------------------------------------ | ----------------------------------- |
| `j`, `s`              | scroll down                                                  | scrollDown                          |
| `k`, `w`              | scroll up                                                    | scrollUp                            |
| `h`                   | scroll left                                                  | scrollLeft                          |
| `l`                   | scroll right                                                 | scrollRight                         |
| `d`                   | scroll half-page down                                        | scrollPageDown                      |
| unmapped              | scroll full-page down                                        | scrollFullPageDown                  |
| `u`, `e`              | scroll half-page up                                          | scrollPageUp                        |
| unmapped              | scroll full-page up                                          | scrollFullPageUp                    |
| `gg`                  | scroll to the top of the page                                | scrollToTop                         |
| `G`                   | scroll to the bottom of the page                             | scrollToBottom                      |
| `0`                   | scroll to the left of the page                               | scrollToLeft                        |
| `$`                   | scroll to the right of the page                              | scrollToRight                       |
| `#`                   | reset the scroll focus to the main page                      | resetScrollFocus                    |
| `gi`                  | go to first input box                                        | goToInput                           |
| `gI`                  | go to the last focused input box by `gi`                     | goToLastInput                       |
| `zz`                  | center page to current search match (middle)                 | centerMatchH                        |
| `zt`                  | center page to current search match (top)                    | centerMatchT                        |
| `zb`                  | center page to current search match (bottom)                 | centerMatchB                        |
| **Link Hints**        |                                                              |                                     |
| `f`                   | open link in current tab                                     | createHint                          |
| `F`                   | open link in new tab                                         | createTabbedHint                    |
| unmapped              | open link in new tab (active)                                | createActiveTabbedHint              |
| `W`                   | open link in new window                                      | createHintWindow                    |
| `A`                   | repeat last hint command                                     | openLastHint                        |
| `q`                   | trigger a hover event (mouseover + mouseenter)               | createHoverHint                     |
| `Q`                   | trigger a unhover event (mouseout + mouseleave)              | createUnhoverHintc                  |
| `mf`                  | open multiple links                                          | createMultiHint                     |
| unmapped              | edit text with external editor                               | createEditHint                      |
| unmapped              | call a code block with the link as the first argument        | createScriptHint(`<FUNCTION_NAME>`) |
| unmapped              | opens images in a new tab                                    | fullImageHint                       |
| `mr`                  | reverse image search multiple links                          | multiReverseImage                   |
| `my`                  | yank multiple links (open the list of links with P)          | multiYankUrl                        |
| `gy`                  | copy URL from link to clipboard                              | yankUrl                             |
| `gr`                  | reverse image search (google images)                         | reverseImage                        |
| `;`                   | change the link hint focus                                   |                                     |
| **QuickMarks**        |                                                              |                                     |
| `M<*>`                | create quickmark <*>                                         | addQuickMark                        |
| `go<*>`               | open quickmark <*> in the current tab                        | openQuickMark                       |
| `gn<*>`               | open quickmark <*> in a new tab                              | openQuickMarkTabbed                 |
| `gw<*>`               | open quickmark <*> in a new window                           | openQuickMarkWindowed               |
| **Miscellaneous**     |                                                              |                                     |
| `a`                   | alias to ":tabnew google "                                   | :tabnew google                      |
| `.`                   | repeat the last command                                      | repeatCommand                       |
| `:`                   | open command bar                                             | openCommandBar                      |
| `/`                   | open search bar                                              | openSearchBar                       |
| `?`                   | open search bar (reverse search)                             | openSearchBarReverse                |
| unmapped              | open link search bar (same as pressing `/?`)                 | openLinkSearchBar                   |
| `I`                   | search through browser history                               | :history                            |
| `<N>g%`               | scroll <N> percent down the page                             | percentScroll                       |
| `<N>`unmapped         | pass `<N>` keys through to the current page                  | passKeys                            |
| `i`                   | enter insert mode (escape to exit)                           | insertMode                          |
| `r`                   | reload the current tab                                       | reloadTab                           |
| `gR`                  | reload the current tab + local cache                         | reloadTabUncached                   |
| `;<*>`                | create mark <*>                                              | setMark                             |
| `''`                  | go to last scroll position                                   | lastScrollPosition                  |
| `<C-o>`               | go to previous scroll position                               | previousScrollPosition              |
| `<C-i>`               | go to next scroll position                                   | nextScrollPosition                  |
| `'<*>`                | go to mark <*>                                               | goToMark                            |
| `cm`                  | mute/unmute a tab                                            | muteTab                             |
| none                  | reload all tabs                                              | reloadAllTabs                       |
| `cr`                  | reload all tabs but current                                  | reloadAllButCurrent                 |
| `zi`                  | zoom page in                                                 | zoomPageIn                          |
| `zo`                  | zoom page out                                                | zoomPageOut                         |
| `z0`                  | zoom page to original size                                   | zoomOrig                            |
| `z<Enter>`            | toggle image zoom (same as clicking the image on image-only pages) | toggleImageZoom                     |
| `gd`                  | alias to :chrome://downloads<CR>                             | :chrome://downloads<CR>             |
| `ge`                  | alias to :chrome://extensions<CR>                            | :chrome://extensions<CR>            |
| `yy`                  | copy the URL of the current page to the clipboard            | yankDocumentUrl                     |
| `yY`                  | copy the URL of the current frame to the clipboard           | yankRootUrl                         |
| `ya`                  | copy the URLs in the current window                          | yankWindowUrls                      |
| `yh`                  | copy the currently matched text from find mode (if any)      | yankHighlight                       |
| `b`                   | search through bookmarks                                     | :bookmarks                          |
| `p`                   | open the clipboard selection                                 | openPaste                           |
| `P`                   | open the clipboard selection in a new tab                    | openPasteTab                        |
| `gj`                  | hide the download shelf                                      | hideDownloadsShelf                  |
| `gf`                  | cycle through iframes                                        | nextFrame                           |
| `gF`                  | go to the root frame                                         | rootFrame                           |
| `gq`                  | stop the current tab from loading                            | cancelWebRequest                    |
| `gQ`                  | stop all tabs from loading                                   | cancelAllWebRequests                |
| `gu`                  | go up one path in the URL                                    | goUpUrl                             |
| `gU`                  | go to to the base URL                                        | goToRootUrl                         |
| `gs`                  | go to the view-source:// page for the current Url            | :viewsource!                        |
| `<C-b>`               | create or toggle a bookmark for the current URL              | createBookmark                      |
| unmapped              | close all browser windows                                    | quitChrome                          |
| `g-`                  | decrement the first number in the URL path (e.g `www.example.com/5` => `www.example.com/4`) | decrementURLPath                    |
| `g+`                  | increment the first number in the URL path                   | incrementURLPath                    |
| **Tab Navigation**    |                                                              |                                     |
| `gt`, `K`, `R`        | navigate to the next tab                                     | nextTab                             |
| `gT`, `J`, `E`        | navigate to the previous tab                                 | previousTab                         |
| `g0`, `g$`            | go to the first/last tab                                     | firstTab, lastTab                   |
| `<C-S-h>`, `gh`       | open the last URL in the current tab's history in a new tab  | openLastLinkInTab                   |
| `<C-S-l>`, `gl`       | open the next URL from the current tab's history in a new tab | openNextLinkInTab                   |
| `x`                   | close the current tab                                        | closeTab                            |
| `gxT`                 | close the tab to the left of the current tab                 | closeTabLeft                        |
| `gxt`                 | close the tab to the right of the current tab                | closeTabRight                       |
| `gx0`                 | close all tabs to the left of the current tab                | closeTabsToLeft                     |
| `gx$`                 | close all tabs to the right of the current tab               | closeTabsToRight                    |
| `X`                   | open the last closed tab                                     | lastClosedTab                       |
| `t`                   | :tabnew                                                      | :tabnew                             |
| `T`                   | :tabnew <CURRENT URL>                                        | :tabnew @%                          |
| `O`                   | :open <CURRENT URL>                                          | :open @%                            |
| `<N>%`                | switch to tab <N>                                            | goToTab                             |
| `H`, `S`              | go back                                                      | goBack                              |
| `L`, `D`              | go forward                                                   | goForward                           |
| `B`                   | search for another active tab                                | :buffer                             |
| `<`                   | move current tab left                                        | moveTabLeft                         |
| `>`                   | move current tab right                                       | moveTabRight                        |
| `]]`                  | click the "next" link on the page (see nextmatchpattern above) | nextMatchPattern                    |
| `[[`                  | click the "back" link on the page (see previousmatchpattern above) | previousMatchPattern                |
| `gp`                  | pin/unpin the current tab                                    | pinTab                              |
| `<C-6>`               | toggle the focus between the last used tabs                  | lastUsedTab                         |
| **Find Mode**         |                                                              |                                     |
| `n`                   | next search result                                           | nextSearchResult                    |
| `N`                   | previous search result                                       | previousSearchResult                |
| `v`                   | enter visual/caret mode (highlight current search/selection) | toggleVisualMode                    |
| `V`                   | enter visual line mode from caret mode/currently highlighted search | toggleVisualLineMode                |
| unmapped              | clear search mode highlighting                               | clearSearchHighlight                |
| **Visual/Caret Mode** |                                                              |                                     |
| `<Esc>`               | exit visual mode to caret mode/exit caret mode to normal mode |                                     |
| `v`                   | toggle between visual/caret mode                             |                                     |
| `h`, `j`, `k`, `l`    | move the caret position/extend the visual selection          |                                     |
| `y`                   | copys the current selection                                  |                                     |
| `n`                   | select the next search result                                |                                     |
| `N`                   | select the previous search result                            |                                     |
| `p`                   | open highlighted text in current tab                         |                                     |
| `P`                   | open highlighted text in new tab                             |                                     |
| **Text boxes**        |                                                              |                                     |
| `<C-i>`               | move cursor to the beginning of the line                     | beginningOfLine                     |
| `<C-e>`               | move cursor to the end of the line                           | endOfLine                           |
| `<C-u>`               | delete to the beginning of the line                          | deleteToBeginning                   |
| `<C-o>`               | delete to the end of the line                                | deleteToEnd                         |
| `<C-y>`               | delete back one word                                         | deleteWord                          |
| `<C-p>`               | delete forward one word                                      | deleteForwardWord                   |
| unmapped              | delete back one character                                    | deleteChar                          |
| unmapped              | delete forward one character                                 | deleteForwardChar                   |
| `<C-h>`               | move cursor back one word                                    | backwardWord                        |
| `<C-l>`               | move cursor forward one word                                 | forwardWord                         |
| `<C-f>`               | move cursor forward one letter                               | forwardChar                         |
| `<C-b>`               | move cursor back one letter                                  | backwardChar                        |
| `<C-j>`               | move cursor forward one line                                 | forwardLine                         |
| `<C-k>`               | move cursor back one line                                    | backwardLine                        |
| unmapped              | select input text (equivalent to `<C-a>`)                    | selectAll                           |
| unmapped              | edit with Vim in a terminal (need the [cvim_server.py](https://github.com/1995eaton/chromium-vim/blob/master/cvim_server.py) script running for this to work and the VIM_COMMAND set inside that script) | editWithVim                         |

# Command Mode

| Command                             | Description                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| :tabnew (autocomplete)              | open a new tab with the typed/completed search               |
| :new (autocomplete)                 | open a new window with the typed/completed search            |
| :open (autocomplete)                | open the typed/completed URL/google search                   |
| :history (autocomplete)             | search through browser history                               |
| :bookmarks (autocomplete)           | search through bookmarks                                     |
| :bookmarks /<folder> (autocomplete) | browse bookmarks by folder/open all bookmarks from folder    |
| :set (autocomplete)                 | temporarily change a cVim setting                            |
| :chrome:// (autocomplete)           | open a chrome:// URL                                         |
| :tabhistory (autocomplete)          | browse the different history states of the current tab       |
| :command `<NAME>` `<ACTION>`        | aliases :`<NAME>` to :`<ACTION>`                             |
| :quit                               | close the current tab                                        |
| :qall                               | close the current window                                     |
| :restore (autocomplete)             | restore a previously closed tab (newer versions of Chrome only) |
| :tabattach (autocomplete)           | move the current tab to another open window                  |
| :tabdetach                          | move the current tab to a new window                         |
| :file (autocomplete)                | open a local file                                            |
| :source (autocomplete)              | load a cVimrc file into memory (this will overwrite the settings in the options page if the `localconfig` setting had been set previously |
| :duplicate                          | duplicate the current tab                                    |
| :settings                           | open the settings page                                       |
| :nohlsearch                         | clear the highlighted text from the last search              |
| :execute                            | execute a sequence of keys (Useful for mappings. For example, "map j :execute 2j") |
| :buffer (autocomplete)              | change to a different tab                                    |
| :mksession                          | create a new session from the current tabs in the active window |
| :delsession (autocomplete)          | delete a saved session                                       |
| :session (autocomplete)             | open the tabs from a saved session in a new window           |
| :script                             | run JavaScript on the current page                           |
| :togglepin                          | toggle the pin state of the current tab                      |
| :pintab                             | pin the current tab                                          |
| :unpintab                           | unpin the current tab                                        |

 

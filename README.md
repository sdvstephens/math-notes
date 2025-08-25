# math-notes

</div>

This is a series of mathematical note taking systems, python scripts, and neovim configs in order to allow in-real-time—i.e., during lectures—math (and other) notes to be taken, including  near-instant figure drawing and insertion via <a href="https://ipe.otfried.org/">IPE</a>, grading-calculators, trackers, and lecture directory management, all from within the terminal. The entire system and setup was directly and heavily inspired by all the brilliant work of the late <a href="https://castel.dev/">Gilles Castel</a>; as such, I sincerely thank Gilles for his unimaginable impact on my LaTeX and neovim knowledge and workflow. 

## NeoVim Prereqs

<a href="https://github.com/LazyVim/LazyVim">LazyVim</a> is a super-package that is easy to install; the github page guides you through the process. We are going to edit the config, however. 

The first dependency is <a href="https://github.com/lervag/vimtex">vimtex</a> (arguably the most import of the bunch). I'd recommend using sioyek as your primary pdf viewer since it has vim controls. We are not going to use stock installation for the vimtex.lua file, instead we will configue it as such:

```lua
return {
  "lervag/vimtex",
  lazy = false, -- lazy-loading will disable inverse search
  config = function()
    vim.g.vimtex_view_method = "sioyek"
    vim.g.vimtex_view_sioyek_options = "--reuse-window"
    vim.g.vimtex_view_sioyek_exe = "/Applications/sioyek.app/Contents/MacOS/sioyek"
    vim.g.vimtex_compiler_latexmk = {
      aux_dir = "./.latexmk/aux",
      out_dir = "./.latexmk/out",
    }
  end,
  keys = {
    { "<localLeader>1", "", desc = "+vimtex" },
  },
}
```



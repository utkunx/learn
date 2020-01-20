# my ide setup summary 0.10 v
<details>
  <summary>Click to expand!</summary>
  
  ## ide diagram
  1. [kitty](#kitty)
  2. [tmux](#tmux)
     * With some
     * Sub bullets
  3. [nvim](#nvim)
     * plugings
     * Sub bullets
  
</details>


-----

## kitty
<details>
  <summary></summary>
  
  ## kitty
  
  </details>



-----

## tmux
<details>
  <summary>tmux</summary>
  
  ## tmux
  
  </details>



-----

## nvim
<details>
  <summary>nvim</summary>
  
  ## nvim
  
  </details>




After adding this to your vimrc run PlugInstall. This has the limitation that you can't uninstall the extension by using :CocUninstall and that automatic update support is not available.

* coc.nvim

Plug 'neoclide/coc.nvim', {'do': { -> coc#util#install()}}
Plug 'neoclide/coc-snippets', {'do': 'yarn install --frozen-lockfile'}
Plug 'neoclide/coc-tsserver', {'do': 'yarn install --frozen-lockfile'}
Plug 'neoclide/coc-prettier', {'do': 'yarn install --frozen-lockfile'}
Plug 'neoclide/coc-eslint', {'do': 'yarn install --frozen-lockfile'}
Plug 'neoclide/coc-tslint', {'do': 'yarn install --frozen-lockfile'}
Plug 'neoclide/coc-css', {'do': 'yarn install --frozen-lockfile'}
Plug 'neoclide/coc-lists', {'do': 'yarn install --frozen-lockfile'} " mru and stuff
Plug 'neoclide/coc-highlight', {'do': 'yarn install --frozen-lockfile'} " color highlighting

  * coc-actions 1.0.4 ~/.config/coc/extensions/node_modules/coc-actions                                    
  * coc-explorer 0.2.17 ~/.config/coc/extensions/node_modules/coc-explorer                                 
  * coc-git 1.6.16 ~/.config/coc/extensions/node_modules/coc-git                                           
  * coc-highlight 1.2.5 ~/.config/coc/extensions/node_modules/coc-highlight                                
  * coc-todolist 1.1.0 ~/.config/coc/extensions/node_modules/coc-todolist                                  
  * coc-eslint 1.2.4 ~/.config/coc/extensions/node_modules/coc-eslint                                      
  * coc-lists 1.3.6 ~/.config/coc/extensions/node_modules/coc-lists                                        
  * coc-yank 1.1.3 ~/.config/coc/extensions/node_modules/coc-yank                                          
  * coc-syntax 1.2.4 ~/.config/coc/extensions/node_modules/coc-syntax                                      
  * coc-snippets 2.1.17 ~/.config/coc/extensions/node_modules/coc-snippets                                 
  * coc-bookmark 1.0.3 ~/.config/coc/extensions/node_modules/coc-bookmark                                  
  * coc-emmet 1.1.4 ~/.config/coc/extensions/node_modules/coc-emmet                                        
  * coc-prettier 1.1.11 ~/.config/coc/extensions/node_modules/coc-prettier                                 
  * coc-utils 0.0.10 ~/.config/coc/extensions/node_modules/coc-utils                                       
  * coc-project 0.0.8 ~/.config/coc/extensions/node_modules/coc-project                                    
  * coc-tailwindcss 0.4.0 ~/.config/coc/extensions/node_modules/coc-tailwindcss                            
  * coc-vimlsp 0.4.4 ~/.config/coc/extensions/node_modules/coc-vimlsp                                      
  * coc-marketplace 1.7.0 ~/.config/coc/extensions/node_modules/coc-marketplace                            
  + coc-css 1.2.2 ~/.config/coc/extensions/node_modules/coc-css                                            
  + coc-svelte 0.0.2 ~/.config/coc/extensions/node_modules/coc-svelte                                      
  + coc-svg 0.0.13 ~/.config/coc/extensions/node_modules/coc-svg                                           
  + coc-markdownlint 1.0.2 ~/.config/coc/extensions/node_modules/coc-markdownlint                          
  + coc-lit-html 0.2.0 ~/.config/coc/extensions/node_modules/coc-lit-html                                  
  + coc-json 1.2.4 ~/.config/coc/extensions/node_modules/coc-json                                          
  + coc-html 1.2.1 ~/.config/coc/extensions/node_modules/coc-html                                          
  + coc-tsserver 1.4.9 ~/.config/coc/extensions/node_modules/coc-tsserver                                  
  + coc-docker 0.2.1 ~/.config/coc/extensions/node_modules/coc-docker                                      
  + coc-markmap 0.1.4 ~/.config/coc/extensions/node_modules/coc-markmap                                    
  - coc-tabnine 1.2.2 ~/.config/coc/extensions/node_modules/coc-tabnine                                    
  - vscode-svelte-snippets 0.3.0 ~/.config/coc/extensions/node_modules/vscode-svelte-snippets     

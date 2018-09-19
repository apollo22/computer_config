# Shells aliases

## Aliases definitions

The **_docs** files use the $DOCS_EDITOR environment variable, set in **shells**.

I use **global aliases** and **suffix aliases** in shells that support it.

[TODO] Document and implement

Aliases are defined in many files in the **~/.config/shells/aliases** folder :
  - **shells** for aliases used by all shells, loaded by ~/.config/shells/shellsrc and responsible for loading all the _docs aliases. **-- Should no longer exist. --**
  - **<shell_name>** for aliases used by a specific shell, loaded by related <shell_name>rc.
  - **root_folders_variables** set root folders variables and source public, private, personal and professional aliases files described below.**-- Should be renamed shells --**

The following **<name>/access aliases** files set related folders variables, set aliases to quickly access related folders and files and source the files in the related **<name>_functions** folder.
The following **quick_functions** files set short aliases for functions.

The **access_aliases** in the **PROFESSIONAL_FOLDER** source the **<organisation_name>/access_aliases** files in the **PROFESSIONAL_FOLDER**. Those are of the same form that previous **access_aliases** files.

  - PUBLIC_FOLDER/.aliases/
    - **access_aliases**
    - **functions/**
      - **quick_functions**
  - PRIVATE_FOLDER/.aliases/
    - **access_aliases**
    - **functions/**
      - **quick_functions**
  - PERSONAL_FOLDER/.aliases/
    - **access_aliases**
    - **functions/**
      - **quick_functions**
  - CONFIG_FILES

  - PROFESSIONAL_FOLDER/
  - **access_aliases**
  - **<ORGANISATION_NAME>_FOLDER**/
    - **access_aliases**
    - **functions/**
      - **quick_functions**
      

  functions and other aliases
    
shalias = pubalias
<name>falias
<name>dalias


## Unsorted notes

<folder_name>: access folder (with underscores removed)
n<subject>: edit note about subject


v <file>: edit file with vim

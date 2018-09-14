# Shells aliases

## Aliases definitions

The **_docs** files use the $DOCS_EDITOR environment variable, set in **shells**.

I use **global aliases** and **suffix aliases** in shells that support it.

[TODO] Document and implement

Aliases are defined in many files in the **~/.config/shells/aliases** folder :
  - **shells** for aliases used by all shells, loaded by ~/.config/shells/shellsrc and responsible for loading all the _docs aliases. **-- Should no longer exist.**
  - **<shell_name>** for aliases used by a specific shell, loaded by related <shell_name>rc.
shellsrc
  - **root_folders_variables** should be renamed **shells**, set root folders variables and source public, private, personal and professional aliases filese

The following **<name>_access aliases** files set related folders variables, source related **<name>_quick_access** file and set aliases to quickly access related folders and files. At their end, they unset all set folders variables.
The following **<name>_quick_functions** files set short aliases for functions, and source the files in the related **<name>_functions** folder.

The **professional_access_aliases** source the **<organisation_name>_access_aliases** files in the **organisation_aliases** folder. Those are of the same form that previous **_access_aliases** files. Those **<organisation_name>_access_aliases** try to source the related **<organisation_name>_functions** if it exists. 

  - PUBLIC_FOLDER/.aliases/
    - **access_aliases**
    - **quick_functions**
    - **functions/**
  - PRIVATE_FOLDER/.aliases/
    - **access_aliases**
    - **quick_functions**
    - **functions/**
  - PERSONAL_FOLDER/.aliases/
    - **access_aliases**
    - **quick_functions**
    - **functions/**

  - PROFESIONAL_FOLDER/
  - **access_aliases**
  - **<ORGANISATION_NAME>_FOLDER**/
    - **access_aliases**
    - **quick_functions**
    - **functions/**
      

  functions and other aliases
    
shalias = pubalias
<name>falias
<name>dalias


## Unsorted notes

<folder_name>: access folder (with underscores removed)
n<subject>: edit note about subject


v <file>: edit file with vim

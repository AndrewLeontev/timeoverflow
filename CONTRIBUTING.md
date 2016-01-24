Entorno de desarrollo aconsejado (para mac)
===========================================

iTerm2 - un terminal mucho más completo (<http://iterm2.com>). Especialmente recomendado activar
la opción "Working directory -> Reuse previous session's directory" para el perfil por defecto,
para jugar fácilmente con múltiples pestañas en la misma directory.

SublimeText2 - un editor muy muy avanzado (<http://www.sublimetext.com>). Instalar también
PackageControl para luego instalar extensiones de forma muy fácil (seguir instrucciones en
<https://packagecontrol.io/installation#st2>). Otro editor que promete es Atom (<https://atom.io>)
aunque no es tan maduro, tiene unos grandes desarrolladores detrás. Ambos permiten - y es muy
importante - evitar que se cuelen TABs en el código.

Homebrew - para instalar todo tipo de paquetes adicionales (<http://brew.sh>).

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

YADR - una biblioteca de shortcuts y mejoras para zsh y la línea de comando de ruby
(<https://github.com/skwp/dotfiles>). No hacen falta las opciones para `vim`, sobretodo si uno
no está acostumbrado a vim, la opción "vimification of command line tools" puede ser mortal!

    sh -c "`curl -fsSL https://raw.githubusercontent.com/skwp/dotfiles/master/install.sh`" -s ask
    
Instalar varios paquetes por medio de homebrew

    brew install git rbenv ruby-build postgresql
    
Instalar ruby

    rbenv install 2.2.0
    rbenv global 2.2.0
    
Añadir la siguiente línea al fichero `.profile` para tener rbenv activado) y reiniciar
el terminal.

    eval "$(rbenv init -)"


Actualizar rubygems e instalar bundler

    gem update --system
    gem install bundler
    

Como instalar docker y containers en mac (WIP):
===============================================

1. instalar lo necesario para compilar cosas (esto es lo mismo que el paquete `build-essential` en debian):

  * Xcode: ejecutar `pkgutil --pkg-info=com.apple.pkg.CLTools_Executables` en consola.
    si dice que `No receipt for 'com.apple.pkg.CLTools_Executables'`, instalar Xcode desde
    <https://developer.apple.com/xcode/>

2. instalar pip: `sudo easy_install pip` (para el python de sistema)
3. instalar ansible: `sudo pip install ansible`
4. ejecutar:
    >  ansible-playbook -i provisioning/hosts provisioning/development-osx.yml --ask-become-pass

Si se veiran problemas de "gem not found" y similares, asegurarse de no tener
`export RUBYGEMS_GEMDEPS="-"` en ningún fichero de inicio:
- `.bashrc`
- `.zshrc`
- `.zprofile`
- `.profile`
- `.bash_profile`
- `.zlogin`
- `.my_init_var_script`

etc

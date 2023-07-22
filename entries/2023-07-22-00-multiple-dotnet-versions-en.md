# How to setup multiple dotnet versions

```
// if exists, remove
sudo rm -r /usr/share/dotnet/

@Home
wget https://dot.net/v1/dotnet-install.sh -O dotnet-install.sh

// multiple versions
sh ./dotnet-install.sh -v 7.0.306
//  or https://github.com/dotnet/core/blob/main/release-notes/8.0/install.md
sh ./dotnet-install.sh --channel 8.0.1xx --quality preview;

// make `donet` usable from anywhere 
export DOTNET_ROOT=$HOME/.dotnet
export PATH=$PATH:$DOTNET_ROOT:$DOTNET_ROOT/tools

// use dotnet commands
dotnet --list-sdks
dotnet --version

// create new project directory and move into it
mkdir test-fs
cd test-fs

// test the local donet status
dotnet --list-sdks
dotnet --version

// specify the local dotnet version
dotnet new globaljson --sdk-version $(dotnet --version) --force
or
dotnet new globaljson --sdk-version 7.0.306 --force
dotnet new globaljson --sdk-version 8.0.100-preview.6.23330.14 --force

//new project will be created with the speficied version: check *.fsproj for TargetFramework
dotnet new console --language F#
code-insiders --profile fsharp ./

the ionide configuration for dotnet root should be blank



```
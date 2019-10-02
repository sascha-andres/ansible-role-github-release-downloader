# GitHub release downloader

This Ansible role allows to download a GitHub release and place it in a well known directory.

It remembers the last installed version so it will not downlad a release again

## Usage

Let's assume a yaml file like this:

    ---

    - name: fonts || firacode || download
      include_role:
        name: sascha_andres.ansible_role_github_release_downloader
    - name: do something
      debug:
        msg: "up to you"

And you include it somewhere like this:

    - name: fonts || firacode
      include: "firacode.yaml"
      vars:
        github_repository: tonsky/FiraCode
        save_path: "{{ home_dir }}/tmp"
        github_download_url: "https://github.com/{{ github_repository }}/releases/download/{{ github_repository_version }}/FiraCode_{{     github_repository_version }}.zip"
        storage_version_path: "{{ home_dir }}/.ansible_deploy/font-firacode"
        storage_version_filename: "version"
    
It would place the unpacked files in `{{ home_dir }}/tmp` ready to copy them to the right place.

## Variables

|Name|Description|
|---|---|
|github_repository|Name of the repository (namespace/repo on github)|
|save_path|where to store/unpack the download|
|github_download_url|the download url|
|github_repository_version|the latet version on github, will be set|
|storage_version_path|where to save the version information|
|storage_version_filename|how to name the file containing the currently installed versino|
|unpack|defaulting to true to unpack the files, set to false if it not packed|

## History

|Version|Description|
|---|---|
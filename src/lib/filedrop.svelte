<script lang="ts">
  import upload from 'svelte-awesome/icons/upload';
  import file_icon from 'svelte-awesome/icons/file'
  import Icon from 'svelte-awesome/components/Icon.svelte';
  import FileDrop from 'svelte-file-dropzone'; 
  import type { Files } from "filedrop-svelte";
  import fileSize from "filesize";
  import dayjs from 'dayjs';
  import localizedFormat from "dayjs/plugin/localizedFormat";
  import { fade, blur, fly, slide, scale } from "svelte/transition";
  import { quintOut } from 'svelte/easing';
  // import tauriapi from '@tauri-apps/api';
  // const { invoke } = tauriapi.tauri;
  // import { open } from "@tauri-apps/api/dialog";

  dayjs.extend(localizedFormat);
  let files: Files= {
    accepted: [],
    rejected: []
  };

  function handleFilesSelect(e) {
    const {acceptedFiles, fileRejections} = e.detail;
    files.accepted = [...acceptedFiles];
    files.rejected = [...fileRejections];
    console.log(files.accepted)
  }
</script>


  <FileDrop on:drop={handleFilesSelect}>
    <div class="file-drop-area">
      <div class="icon-upload">
        <Icon data={upload} style="width: 100%; height: 100%; opacity: 0.5;"/>
      </div>
      <span class="file-msg">drag and drop files here</span>
    </div>
  </FileDrop>
{#if files}
  <h3>Accepted files</h3>

  <ol>
    {#each files.accepted as file}
      <li transition:scale={{ delay:250, duration: 300, easing: quintOut }}> 
        <div class="listContainer">
          <div class="icon-file">
            <Icon data={file_icon} style ="width:100%; height: 100%; opacity:0.5;"/>
          </div>
          <div class = "file-components">
            File Name: {file.name}
          </div>
          <div class = "file-components">
            Size: {fileSize(file.size)}
          </div>
          <div class = "file-components">
            Last Modified: {dayjs(file.lastModified).format('LTS - DD/MM/YYYY')}
          </div>
        </div>

      </li>
    {/each}
  </ol>
{/if}

<style>
    
  .file-drop-area {
    position: relative;
    display: grid;
    grid-template-columns: [col1-start] 25% [col1-end col2-start] 50% [col2-end col3-start] 25% [col3-end];
    grid-template-rows: [row1-start] 70% [row1-end row2-start] 25% [row2-end row3-start] 25% [row3-end];
    align-items: center;
    height: 200px;
    width: 450px;
    max-width: 100%;
    margin: 20px;
    padding: 25px;
    border: 1px dashed rgba(255, 255, 255, 0.4);
    border-radius: 3px;
    transition: 0.2s;
    cursor: pointer;
  }

  .icon-upload{
    width: 150px;
    height: 150px;
    grid-column-start: col2-start;
    grid-column-end: col2-end;
    grid-row-start: row1-start;
    grid-row-end: row1-end;
    justify-self: center;
    align-self: start;
  }

  .icon-file{
    width: 25px;
    height: 25px;
    /* grid-column-start: col2-start;
    grid-column-end: col2-end;
    grid-row-start: row1-start;
    grid-row-end: row1-end;
    justify-self: center;
    align-self: start; */
  }

  .fake-btn {
    background-color: rgba(255, 255, 255, 0.04);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 3px;
    padding: 8px 15px;
    margin-right: 10px;
    font-size: 12px;
    text-transform: uppercase;
    grid-column-start: col2-start;
    grid-column-end: col2-end;
    grid-row-start: row2-start;
    grid-row-end: row2-end;
    justify-self: center;
    align-self: end;
    
  }

  .file-msg {
    font-size: small;
    font-weight: 300;
    line-height: 1.4;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    grid-column-start: col2-start;
    grid-column-end: col2-end;
    grid-row-start: row3-start;
    grid-row-end: row3-end;
    justify-self: center;
  }
  h3 {
    margin: 10px;
  }

  ol {
    height: 16rem;
  }
  li{
    font-size: 1.5rem;
    
    /* transform: translateX(100%);
    transition: transform 0.5s, opacity 2s;
    opacity: 0; */
  }

  .file-components{
    font-size: small;
    font-weight: 300;
    line-height: 1.4;
    white-space: nowrap;
    overflow: hidden;
  }

</style>
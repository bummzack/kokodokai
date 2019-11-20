<script>
  import {send, receive} from '../_helpers/crossfade.js';
  export let title;
</script>

<h1 out:send="{{key: 'h1'}}" in:receive="{{key: 'h1'}}">{title}</h1>

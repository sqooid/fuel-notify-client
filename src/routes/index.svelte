<script lang="ts">
  import { TextInput, Button, Select } from 'svui'
  const states = [
    'sydney',
    'melbourne',
    'brisbane',
    'perth',
    'adelaide',
    'canberra',
    'hobart',
    'darwin',
  ]
  const options = states.map((state) => {
    return {
      value: state,
      title: state.charAt(0).toUpperCase() + state.slice(1),
    }
  })

  let email = ''
  let emailValid = true
  let state = ''
  let stateValid = true

  const onSubscribe = () => {
    emailValid = /^.+@.+\..+/.test(email) && !!email.length
    stateValid = !!state.length
  }
</script>

<svelte:head><title>Fuel Notify</title></svelte:head>
<div id="index">
  <TextInput placeholder="Email" bind:value={email} invalid={!emailValid} />
  <Select {options} bind:value={state} />
  <Button primary label="Subscribe" on:click={onSubscribe} />
</div>

<style>
  #index {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 10px;
  }
</style>

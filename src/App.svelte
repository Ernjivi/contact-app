<script>

  import Header from './components/Header.svelte';

  import { auth } from './firebase';
  import { authState } from 'rxfire/auth';

  import { user } from './stores.js';

  import ContactList from './components/ContactList.svelte';
  import ContactForm from './components/ContactForm.svelte';

  const unsubscribe = authState(auth).subscribe(
    u => user.update(() => ({...u})));

</script>

<style></style>

<Header />
<ContactForm /> 
<ContactList />


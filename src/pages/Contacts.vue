<template>
  <q-page class="bg-brown-1 column">
    <h2 class="heading">Contacts!</h2>
    <div class="row no-wrap items-center justify-around q-gutter-sm">
      <q-chip
        :ripple="false"
        color="primary"
        text-color="white"
        icon="telegram"
      >
        @RukiMary
      </q-chip>
      <q-chip :ripple="false" color="primary" text-color="white" icon="email">
        rookie.mary@gmail.com
      </q-chip>
      <q-chip
        :ripple="false"
        color="primary"
        text-color="white"
        icon="explicit"
      >
        behance.net/rookiemary
      </q-chip>
      <q-chip :ripple="false" color="primary" text-color="white" icon="discord">
        rukimary
      </q-chip>
      <q-chip
        :ripple="false"
        color="primary"
        text-color="white"
        icon="markunread_mailbox"
      >
        PO Box St. Petersburg
      </q-chip>
    </div>
  </q-page>
</template>

<script></script>

<style>
.heading {
  display: flex;
  justify-content: center;
}
</style>

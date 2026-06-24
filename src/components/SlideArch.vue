<template>
  <section class="slide">
    <div class="container">
      <span class="badge">Architettura</span>
      <h2>Architettura del progetto</h2>
      <p class="subtitle">
        Macchina a stati che separa UI e logica in moduli indipendenti
      </p>

      <div class="arch-diagram">
        <div class="arch-row">
          <div class="arch-box highlight">
            <div class="label">Entry</div>
            <div class="name">main.rs</div>
            <div class="desc">Setup terminale ed event loop</div>
          </div>
        </div>

        <div class="arch-arrow">&darr;</div>

        <div class="arch-row">
          <div class="arch-box">
            <div class="label">GUI Layer</div>
            <div class="name">gui/</div>
            <div class="desc">
              App (state machine) &middot; ConnectionList &middot; NewConnection<br>
              QueryPage &middot; HistoryPage &middot; InputOverlay
            </div>
          </div>
          <div class="arch-box">
            <div class="label">Business Logic</div>
            <div class="name">utils/</div>
            <div class="desc">
              ConnectionManager &middot; QueryExecutor<br>
              Driver Postgres / MySQL / SQLite
            </div>
          </div>
        </div>

        <div class="arch-arrow">&darr;</div>

        <div class="arch-row">
          <div class="arch-box"><div class="label">Database</div><div class="name">PostgreSQL</div></div>
          <div class="arch-box"><div class="label">Database</div><div class="name">MySQL</div></div>
          <div class="arch-box"><div class="label">Database</div><div class="name">MariaDB</div></div>
          <div class="arch-box"><div class="label">Database</div><div class="name">SQLite</div></div>
        </div>
      </div>

      <p class="arch-note">
        Transizioni di stato: ConnectionList &rarr; NewConnection &sol; QueryPage &rarr; History
      </p>
    </div>
  </section>
</template>

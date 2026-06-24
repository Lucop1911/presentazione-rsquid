<template>
  <section class="slide">
    <div class="container">
      <span class="badge">Features</span>
      <h2>Gestione connessioni</h2>
      <p class="subtitle">Crea, modifica, elimina e gestisci connessioni a database</p>

      <div class="feature-grid">
        <div class="feature-card">
          <div class="img-wrap">
            <img src="/lista_connessioni.webp" alt="Lista connessioni">
          </div>
          <div class="feature-body">
            <h3>Lista connessioni</h3>
            <p>Elenco di tutte le connessioni salvate con navigazione tramite frecce.</p>
          </div>
        </div>
        <div class="feature-card">
          <div class="img-wrap">
            <img src="/nuova_connessione.webp" alt="Nuova connessione">
          </div>
          <div class="feature-body">
            <h3>Nuova / Modifica connessione</h3>
            <p>Form per inserire nome, tipo database, host, porta, credenziali.</p>
          </div>
        </div>
      </div>

      <ul class="feature-list">
        <li>Supporto PostgreSQL, MySQL, MariaDB, SQLite</li>
        <li>Connessioni salvate su disco (JSON)</li>
        <li>Test di connessione con timeout</li>
        <li>Modifica e cancellazione connessioni</li>
      </ul>
    </div>
  </section>
</template>

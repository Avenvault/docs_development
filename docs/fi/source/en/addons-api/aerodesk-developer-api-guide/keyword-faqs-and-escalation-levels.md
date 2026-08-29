# Avainsana FAQs & Escalation Levels

Hallitse avainsanoilla laukaistuja automaattisia vastauksia ja lippujen eskalointiketjuja suoraan configin kautta käyttäen `getApi()`-koukkua.

- Lisää FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Avaa lippu hyvitystä varten.");`
- Hae FAQ: `getApi().getConfig().tickets.keywordFaqs.get ("refund");`
- Muokkaa FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Uusi palautuskäytäntö");`
- Poista FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("hyvitys");`
- Hae skaalaus: `getApi().getConfig().tickets.escalationLevels.get(0)`
- Lisää skaalaus: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager Review", "billing", "1122334455"));`
- Poista skaalaus: `getApi().getConfig().tickets.escalationLevels.removef (taso -> level.levelName.equals("Manager Review");`

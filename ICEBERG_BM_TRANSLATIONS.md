# Iceberg AI Solutions — Bahasa Malaysia Translations
**All new sections · V2 Website Expansion**

---

## How the BM Toggle Works

Each text element gets a `data-en` and `data-bm` attribute. The lang toggle JS swaps `innerHTML` based on which is active. Add this to the existing lang toggle script.

```js
// Replace the existing lang toggle with this enhanced version
document.querySelectorAll('.lang button').forEach(b => {
  b.addEventListener('click', () => {
    document.querySelectorAll('.lang button').forEach(x => x.classList.remove('on'));
    b.classList.add('on');
    const lang = b.textContent.trim() === 'BM' ? 'bm' : 'en';
    document.querySelectorAll('[data-en]').forEach(el => {
      el.innerHTML = el.getAttribute('data-' + lang) || el.getAttribute('data-en');
    });
  });
});
```

---

## Existing Sections — BM for locked copy

### Hero
```
data-en: "Most organisations only see 10% of what AI can do."
data-bm: "Kebanyakan organisasi hanya nampak 10% daripada apa yang AI boleh lakukan."

data-en: "We build the 90% underneath — the automation infrastructure that enterprise and government rely on."
data-bm: "Kami bina 90% di bawah — infrastruktur automasi yang diikhlas oleh perusahaan dan kerajaan."

data-en: "Book a discovery session"
data-bm: "Tempah sesi penemuan"

data-en: "Trusted by"
data-bm: "Dipercayai oleh"
```

### Section 01 · Malaysian AI Imperative
```
data-en: "Malaysia has already moved. The question is how deep you go."
data-bm: "Malaysia sudah bergerak. Persoalannya seberapa dalam anda menyelam."

data-en: "Malaysian businesses already using AI, with adoption jumping 35% in a single year."
data-bm: "Perniagaan Malaysia sudah menggunakan AI, dengan penggunaan melonjak 35% dalam setahun."

data-en: "Of Malaysian businesses using AI remain stuck at basic efficiency tasks."
data-bm: "Perniagaan Malaysia yang menggunakan AI masih terkandas pada tugas kecekapan asas."

data-en: "Of Malaysian CEOs believe AI will determine their competitive advantage within the next 24 months."
data-bm: "CEO Malaysia percaya AI akan menentukan kelebihan daya saing mereka dalam 24 bulan akan datang."
```

---

## New Sections — Full BM Copy

### Section 02b · ILMU Sovereign Advantage

| Element | English | Bahasa Malaysia |
|---|---|---|
| Section label | `02b · Powered by ILMU` | `02b · Dikuasakan oleh ILMU` |
| Heading | `Malaysia's AI. Not rented. Sovereign.` | `AI Malaysia. Bukan dipinjam. Berdaulat.` |
| Body para 1 | `Most AI vendors in Malaysia route your data through foreign infrastructure — US, Singapore, EU. Their compliance is borrowed. Their Bahasa Melayu is approximate.` | `Kebanyakan vendor AI di Malaysia mengalirkan data anda melalui infrastruktur asing — AS, Singapura, EU. Pematuhan mereka dipinjam. Bahasa Melayu mereka tidak tepat.` |
| Body para 2 | `Iceberg operates differently. Through our strategic collaboration with YTL AI Labs, every system we deploy can run on ILMU — Malaysia's first homegrown multimodal LLM, recognised by the Prime Minister and Ministry of Digital as a national capability.` | `Iceberg beroperasi secara berbeza. Melalui kerjasama strategik kami dengan YTL AI Labs, setiap sistem yang kami terapkan boleh berjalan pada ILMU — model bahasa besar multimodal buatan Malaysia yang pertama, diiktiraf oleh Perdana Menteri dan Kementerian Digital sebagai keupayaan nasional.` |

**ILMU Stats:**
| English | Bahasa Malaysia |
|---|---|
| `#1 on MalayMMLU benchmark — outperforms all frontier models in Bahasa Melayu` | `#1 pada penanda aras MalayMMLU — mengatasi semua model frontier dalam Bahasa Melayu` |
| `GPT-4o performance matched on global benchmarks, hosted entirely within Malaysia` | `Prestasi setanding GPT-4o pada penanda aras global, dihoskan sepenuhnya di Malaysia` |
| `5 languages fluent — English, Bahasa Melayu, Manglish, Kelantanese, Bahasa Istana` | `Fasih 5 bahasa — Inggeris, Bahasa Melayu, Manglish, dialek Kelantan, Bahasa Istana` |

**ILMU Cards:**
| Card Title (EN) | Card Title (BM) | Card Body (EN) | Card Body (BM) |
|---|---|---|---|
| Data never leaves Malaysia | Data tidak pernah meninggalkan Malaysia | Dihoskan di YTL AI Cloud. Data rakyat anda, rekod institusi anda — di bumi Malaysia. | Dihoskan di YTL AI Cloud. Data warganegara anda, rekod institusi anda — di tanah Malaysia. |
| AIGE-aligned by default | Selaras AIGE secara lalai | Seven-principle National AI Governance and Ethics framework built into every deployment, not retrofitted. | Rangka kerja Tadbir Urus dan Etika AI Nasional tujuh prinsip dibina dalam setiap penerapan, bukan ditambah kemudian. |
| Bilingual + dialect native | Dwibahasa + dialek asli | No translation approximation. ILMU speaks Malaysian — including Manglish and Kelantanese — natively. | Tiada anggaran terjemahan. ILMU bertutur Malaysia — termasuk Manglish dan dialek Kelantan — secara asli. |
| Procurement compliant | Patuh perolehan | For GLCs, government agencies, and regulated industries — sovereign AI is a procurement requirement, not a preference. | Untuk GLC, agensi kerajaan, dan industri terkawal — AI berdaulat adalah keperluan perolehan, bukan pilihan. |

---

### Section 03b · Problems We Solve

| Element | English | Bahasa Malaysia |
|---|---|---|
| Section label | `03b · The operational reality` | `03b · Realiti operasi` |
| Heading | `The issue is not effort. It is infrastructure.` | `Masalahnya bukan usaha. Ia adalah infrastruktur.` |
| Body | `The volume, timing, and channel diversity of citizen and customer communication today has outpaced what any team can consistently manage without automated infrastructure underneath.` | `Jumlah, masa, dan kepelbagaian saluran komunikasi warganegara dan pelanggan hari ini telah melampaui apa yang mana-mana pasukan boleh urus secara konsisten tanpa infrastruktur automasi di bawahnya.` |

**Problem Cards:**
| # | Title (EN) | Title (BM) | Body (EN) | Body (BM) |
|---|---|---|---|---|
| 01 | The Speed Gap | Jurang Kelajuan | A citizen or customer who enquires is in a decision window that closes in minutes. The average organisation responds in over 42 hours. By then, the moment has passed. | Warganegara atau pelanggan yang bertanya berada dalam tetingkap keputusan yang ditutup dalam minit. Purata organisasi bertindak balas dalam lebih 42 jam. Pada masa itu, momentumnya sudah hilang. |
| 02 | After-Hours Demand | Permintaan Luar Waktu | WhatsApp messages arrive at 11PM. Citizen enquiries come on weekends. Organisations that only respond during staffed hours are unavailable for the majority of hours their stakeholders are active. | Mesej WhatsApp tiba pukul 11 malam. Pertanyaan warganegara datang pada hujung minggu. Organisasi yang hanya bertindak balas semasa waktu kakitangan tidak tersedia untuk majoriti jam pemangku kepentingan mereka aktif. |
| 03 | Leads Never Followed Up | Prospek Tidak Ditindaklanjuti | Nearly a third of all leads that express interest receive no follow-up. The marketing spend to generate them has been paid. The return is zero. | Hampir satu pertiga daripada semua prospek yang menyatakan minat tidak menerima susulan. Perbelanjaan pemasaran untuk menjana mereka telah dibayar. Pulangan adalah sifar. |
| 04 | Service That Doesn't Scale | Perkhidmatan Tidak Berskala | The same question asked by 200 customers gets 200 different answers from different staff, at different times, with different quality. Volume grows. Consistency does not. | Soalan yang sama yang ditanya oleh 200 pelanggan mendapat 200 jawapan berbeza daripada kakitangan berbeza, pada masa berbeza, dengan kualiti berbeza. Jumlah bertambah. Konsistensi tidak. |
| 05 | Fragmented Channels | Saluran Berpecah | WhatsApp, website forms, Instagram DMs, Facebook Messenger, phone, email — each managed by a different person on a different platform. No unified view of the citizen or customer. | WhatsApp, borang laman web, DM Instagram, Facebook Messenger, telefon, e-mel — setiap satu diuruskan oleh orang berbeza pada platform berbeza. Tiada pandangan bersatu tentang warganegara atau pelanggan. |
| 06 | Data Without Decision | Data Tanpa Keputusan | Operations generate enormous quantities of data — call logs, enquiry patterns, conversion ratios, service gaps. Most of it is never structured, never reviewed, and never converted into a decision. | Operasi menjana kuantiti data yang besar — log panggilan, corak pertanyaan, nisbah penukaran, jurang perkhidmatan. Kebanyakannya tidak pernah berstruktur, tidak pernah disemak, dan tidak pernah ditukarkan kepada keputusan. |

---

### Section 03c · Industries Served

| Element | English | Bahasa Malaysia |
|---|---|---|
| Section label | `03c · Industries served` | `03c · Industri yang dilayani` |
| Heading | `Deployed across six sectors. Real operations.` | `Diterapkan merentas enam sektor. Operasi sebenar.` |

**Industry Cards:**
| # | Title (EN) | Title (BM) | Body (EN) | Body (BM) |
|---|---|---|---|---|
| 01 | Government & Public Sector | Kerajaan & Sektor Awam | Active engagements with MOHE on AI competition pre-screening; MBJB on citizen voice agent CRM; federal foundation operational automation. | Penglibatan aktif dengan MOHE untuk pra-saringan pertandingan AI; MBJB untuk CRM ejen suara warganegara; automasi operasi yayasan persekutuan. |
| 02 | Federal Foundations & NGOs | Yayasan Persekutuan & NGO | MyKasih Foundation and Wassiyah process automation, beneficiary engagement workflows, and structured data acquisition supporting national-scale programmes. | Automasi proses MyKasih Foundation dan Wassiyah, aliran kerja penglibatan penerima manfaat, dan pemerolehan data berstruktur menyokong program berskala nasional. |
| 03 | Healthcare | Penjagaan Kesihatan | AI Receptionist and Chatbot for appointment booking, patient enquiry handling, and post-visit follow-up. Available 24/7 across WhatsApp and web with full clinical-language calibration. | Penerima Tetamu AI dan Chatbot untuk tempahan temujanji, pengendalian pertanyaan pesakit, dan susulan selepas lawatan. Tersedia 24/7 merentasi WhatsApp dan web dengan kalibrasi bahasa klinikal penuh. |
| 04 | Financial Services | Perkhidmatan Kewangan | AI Outbound Caller for life insurance and renewal campaigns — hundreds of simultaneous calls without additional headcount. Bilingual qualification with full audit trail for compliance. | Pemanggil Keluar AI untuk kempen insurans hayat dan pembaharuan — ratusan panggilan serentak tanpa kakitangan tambahan. Kelayakan dwibahasa dengan jejak audit penuh untuk pematuhan. |
| 05 | Hospitality & Property | Perhotelan & Hartanah | Bahasa Melayu and Bahasa Indonesia localisation for international AI voice partners serving hotel clients. Property developer deployments for sales qualification and post-handover service. | Penyetempatan Bahasa Melayu dan Bahasa Indonesia untuk rakan kongsi suara AI antarabangsa yang melayani klien hotel. Penerapan pemaju hartanah untuk kelayakan jualan dan perkhidmatan selepas serah terima. |
| 06 | Fitness & Wellness | Kecergasan & Kesihatan | MetaXFitness deployment — AI Outbound Caller re-engaging previous clients at subscription end, collecting feedback, and offering renewal without manual follow-up from trainers. | Penerapan MetaXFitness — Pemanggil Keluar AI menghubungi semula klien terdahulu pada penghujung langganan, mengumpul maklum balas, dan menawarkan pembaharuan tanpa susulan manual daripada jurulatih. |

---

### Section 04b · Competitor Comparison

| Element | English | Bahasa Malaysia |
|---|---|---|
| Section label | `04b · How we compare` | `04b · Perbandingan kami` |
| Heading | `Most vendors are building on the surface.` | `Kebanyakan vendor membina di permukaan.` |
| Col header: Capability | `Capability` | `Keupayaan` |
| Col header: Typical vendor | `Typical Malaysian AI Vendor` | `Vendor AI Malaysia Biasa` |
| Col header: Iceberg | `Iceberg AI Solutions` | `Iceberg AI Solutions` |

**Comparison Rows:**
| Feature (EN) | Feature (BM) | Them (EN) | Them (BM) | Us (EN) | Us (BM) |
|---|---|---|---|---|---|
| LLM Backbone | Teras LLM | Foreign model (GPT, Gemini, Claude) via API | Model asing (GPT, Gemini, Claude) melalui API | ILMU sovereign LLM via YTL AI Labs collaboration | LLM berdaulat ILMU melalui kerjasama YTL AI Labs |
| Data Hosting | Pengehosan Data | US, Singapore, or EU data centres | Pusat data AS, Singapura, atau EU | YTL AI Cloud, Malaysia — data does not leave the country | YTL AI Cloud, Malaysia — data tidak meninggalkan negara |
| Bahasa Melayu Performance | Prestasi Bahasa Melayu | Approximate; trained on translated data | Anggaran; dilatih pada data terjemahan | Best-in-class — ILMU is #1 on MalayMMLU | Terbaik — ILMU #1 pada MalayMMLU |
| AIGE Compliance | Pematuhan AIGE | Not addressed | Tidak ditangani | AIGE seven-principle alignment built in by design | Penjajaran tujuh prinsip AIGE dibina secara reka bentuk |
| Engagement Model | Model Penglibatan | Project handover, then on your own | Serah projek, kemudian anda urus sendiri | Managed end-to-end with monthly KPI review | Diurus hujung ke hujung dengan semakan KPI bulanan |
| Deployment Time | Masa Penerapan | 3 to 6 months typical | 3 hingga 6 bulan biasanya | Under 14 days from discovery to live | Kurang 14 hari dari penemuan hingga beroperasi |
| Voice + Chat + Workflow | Suara + Chat + Aliran Kerja | Single channel typically | Satu saluran biasanya | Unified multi-agent architecture | Seni bina multi-ejen bersatu |

---

### Section 06 · Team

| Element | English | Bahasa Malaysia |
|---|---|---|
| Section label | `06 · The team` | `06 · Pasukan kami` |
| Heading | `A focused founding team. No intermediaries.` | `Pasukan pengasas yang fokus. Tiada perantara.` |
| Body | `Every client engagement is handled directly by the people who built the system.` | `Setiap penglibatan klien dikendalikan terus oleh orang yang membina sistem tersebut.` |
| Firdhaus role | `Co-Founder & CEO` | `Pengasas Bersama & Ketua Pegawai Eksekutif` |
| Firdhaus bio | `Enterprise engagement, commercial structuring, and government relations. Lead on partnership development including the YTL AI Labs collaboration.` | `Penglibatan perusahaan, penstrukturan komersial, dan hubungan kerajaan. Peneraju pembangunan perkongsian termasuk kerjasama YTL AI Labs.` |
| Avvienash role | `Co-Founder & COO` | `Pengasas Bersama & Ketua Pegawai Operasi` |
| Avvienash bio | `Technology and Operations. Full-stack architecture, infrastructure deployment, and integration engineering across CRM, ERP, telephony, and cloud environments.` | `Teknologi dan Operasi. Seni bina penuh-tindanan, penerapan infrastruktur, dan kejuruteraan integrasi merentasi CRM, ERP, telefoni, dan persekitaran awan.` |
| Navientharan role | `Co-Founder & CTO` | `Pengasas Bersama & Ketua Pegawai Teknologi` |
| Navientharan bio | `Lead AI Engineer. Multi-agent system design, ILMU and frontier model integration, voice agent engineering, and AIGE-aligned governance implementation.` | `Jurutera AI Utama. Reka bentuk sistem multi-ejen, integrasi model ILMU dan frontier, kejuruteraan ejen suara, dan pelaksanaan tadbir urus selaras AIGE.` |

---

### Service Labels in Iceberg (svc5–svc8)

| Service | Heading (EN) | Heading (BM) | Description (EN) | Description (BM) |
|---|---|---|---|---|
| svc5 | Enterprise Workflow Automation | Automasi Aliran Kerja Perusahaan | Multi-agent pipelines that qualify, route, process, and escalate cases end-to-end. Human involvement triggered only at moments of genuine value. | Saluran paip multi-ejen yang menilai, menghalakan, memproses, dan meningkatkan kes dari hujung ke hujung. Penglibatan manusia hanya dicetuskan pada saat yang benar-benar bernilai. |
| svc6 | Interactive AI Personas & Avatars | Persona & Avatar AI Interaktif | Custom AI personas with bespoke voice, personality, and domain knowledge. Deployed on kiosks, hologram displays, and exhibition installations. | Persona AI tersuai dengan suara, personaliti, dan pengetahuan domain yang direka khas. Diterapkan pada kiosk, paparan hologram, dan pemasangan pameran. |
| svc7 | Multimodal Voice + Vision | Suara + Penglihatan Multimodal | Process text, voice, and image input within a single conversation thread. Built on ILMU's native multimodal architecture. | Memproses input teks, suara, dan imej dalam satu utas perbualan. Dibina pada seni bina multimodal asli ILMU. |
| svc8 | Sovereign Governance Layer | Lapisan Tadbir Urus Berdaulat | AIGE seven-principle alignment built into every deployment. Per-decision audit logs. Human-in-the-loop checkpoints. | Penjajaran tujuh prinsip AIGE dibina dalam setiap penerapan. Log audit setiap keputusan. Titik semak manusia dalam gelung. |

---

## Implementation Pattern

For every text node that needs translation, apply the `data-en` / `data-bm` pattern:

```html
<!-- Example: Section heading -->
<h2
  data-en="Malaysia's AI. Not rented. Sovereign."
  data-bm="AI Malaysia. Bukan dipinjam. Berdaulat."
>
  Malaysia's AI. Not rented. <span class="emph">Sovereign.</span>
</h2>

<!-- Example: Paragraph -->
<p
  data-en="Most AI vendors in Malaysia route your data through foreign infrastructure."
  data-bm="Kebanyakan vendor AI di Malaysia mengalirkan data anda melalui infrastruktur asing."
>
  Most AI vendors in Malaysia route your data through foreign infrastructure.
</p>
```

**Note:** For elements with inner `<span class="emph">` tags, the full innerHTML including the span needs to be in the data attribute:
```html
data-en="The issue is not effort. It is <span class='emph'>infrastructure.</span>"
data-bm="Masalahnya bukan usaha. Ia adalah <span class='emph'>infrastruktur.</span>"
```

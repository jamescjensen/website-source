<template>
  <expandable-area icon-size="20px">
    <template #title> <span class="text-title">Job History</span></template>

    <div class="content-stack">
      <template v-for="(job, index) in jobs" :key="job.company">
        <expandable-area icon-size="18px">
          <template #title>
            <span class="text-title-subsection inline-spacing">
              {{ job.company }}
            </span>

            <span class="text-subtitle-subsection inline-spacing">
              {{ job.title }}
            </span>

            <span
              class="text-subtitle-subsection"
              :style="{ fontStyle: 'italic' }"
            >
              {{ job.dateRange }}
            </span>
          </template>

          <div class="content-stack">
            <div>
              {{ job.description }}
            </div>

            <div class="skill-list">
              <v-chip
                v-for="skill in job.skills"
                :key="skill"
                class="skill-chip"
                density="compact"
                size="small"
              >{{ skill }}</v-chip>
            </div>

            <template v-if="job.projects.length > 0">
              <expandable-area class="projects-area" :initial-expanded="false">
                <template #title> Projects </template>

                <masonry-grid>
                  <template
                    v-for="project in job.projects"
                    :key="project.title"
                  >
                    <div>
                      <project-card :project="project" />
                    </div>
                  </template>
                </masonry-grid>
              </expandable-area>
            </template>
          </div>

          <template v-if="index !== jobs.length - 1">
            <v-divider class="job-divider" />
          </template>
        </expandable-area>
      </template>
    </div>
  </expandable-area>
</template>

<script setup lang="ts">
  import ExpandableArea from '@/components/ExpandableArea.vue'
  import MasonryGrid from '@/components/MasonryGrid.vue'
  import ProjectCard, { type Project } from './ProjectCard.vue'

  type Job = {
    company: string
    description: string
    title: string
    dateRange: string
    imageUrl?: string
    skills: string[]
    projects: Project[]
  }

  const jobs: Job[] = [
    {
      company: 'Glassdome, Inc.',
      title: 'Head of Backend Software Engineering',
      dateRange: 'Oct 2024 - Present',
      description:
        'Seoul, South Korea. Glassdome builds industrial SaaS for manufacturing monitoring and product carbon footprints. Designed and developed Go backend systems, carbon footprint products, data-exchange integrations, access controls, and customer-facing APIs. Improved time-series query performance and database costs, and maintained production Kubernetes infrastructure on AWS with over 99.99% reported uptime over the past year. Assumed engineering leadership following the Director of Engineering’s departure, managing an 11-person engineering organization and reporting to the CEO. Owned roadmaps and delivery, working with domain experts, product, and design to translate complex requirements into technical designs and prioritized work.',
      skills: [
        'Go',
        'AWS',
        'Kubernetes',
        'Protobuf',
        'Postgres',
        'TimescaleDB',
        'Clickhouse',
      ],
      projects: [
        {
          title: 'Agathon',
          description:
            'Coordinated delivery of a new customer’s 27-point requirements list, clarifying requirements and prioritizing work with the customer success and solution deployment team. Trained a newly full-stack engineer and the new CTO on the backend codebase. Implemented electronic signatures with token issuance and validation, company-level opt-in, and group-level signing permissions, disabled by default for other customers. Also implemented tag grouping, alarm comments, and historian refresh configuration.',
          skills: ['Go', 'AWS', 'Kubernetes'],
        },
        {
          title: 'Certifications',
          description:
            'Represented engineering for ISO/IEC 27001:2022 and SOC 2 Type II renewal audits and a new TISAX certification. ISO/IEC 27001:2022 renewal was achieved; the SOC 2 and TISAX processes remain ongoing.',
          skills: ['ISO/IEC 27001', 'SOC 2', 'TISAX'],
        },
        {
          title: 'Cofinity-X Data Space Accelerator Program',
          description:
            'Supported customer onboarding and product carbon footprint (PCF) interoperability for a German government-funded program promoting Catena-X adoption through Cofinity-X. Updated Glassdome’s integration with connector compatibility and environment configuration developed for Carbonnara, and implemented asynchronous PCF requests. Trained global business development staff on data-sharing workflows and supported onboarding and exchange validation for KGM, Shinsung Autotech, and New Material Industry, whose program procedures were confirmed complete.',
          skills: ['Go', 'Cofinity-X', 'Catena-X'],
          externalLinks: [
            {
              url: 'https://userguide.cofinity-x.com/en/articles/680628-program-overview',
              text: 'Data Space Accelerator program overview',
            },
          ],
        },
        {
          title: 'Carbonnara',
          description:
            'Designed the architecture and helped plan a new product rebuilding Glassdome’s PCF functionality, serving as Scrum Master and later assuming engineering leadership. Completed the initial core rebuild in approximately three months against a six-month target, with testing and production-readiness work continuing afterward. Maintained the roadmap and led cross-functional planning with consulting, product, design, and sales. Built an MCP server for secure AI-client integration, CBAM and EPD frameworks, Cofinity-X data sharing, and spreadsheet-based LCA dataset ingestion with AI-assisted schema mapping. Also implemented live manufacturing data imports, site and unit-process management, report templates, and PDF generation.',
          skills: ['Go', 'AWS', 'Kubernetes', 'MCP', 'Cofinity-X', 'LCA', 'CBAM', 'EPD'],
        },
        {
          title: 'Customer Pipelines',
          description:
            'Managed Python pipelines orchestrated with Airflow for three customers, importing PCF data from spreadsheets and MES data replicated through Airbyte. Helped PCF consultants experiment with data model changes and import new quarterly data.',
          skills: ['Python', 'Airflow', 'Airbyte'],
        },
        {
          title: 'Alarms Rework',
          description:
            'Implemented backend support for reusable monitoring definitions, staged notification policies, and alarm configuration APIs. Migrated valid legacy alarms and added safeguards against changing active alarm configurations.',
          skills: ['Go', 'AWS', 'Kubernetes'],
        },
        {
          title: 'Time-Series Database Migration',
          description:
            'Contributed to a phased ClickHouse-to-TimescaleDB migration covering OEE, shift history, PCF, and live manufacturing metrics, culminating in the shutdown of ClickHouse. Led the shift-history and manufacturing time-series migrations and contributed to the other phases. Reduced selected expensive queries from approximately 12 seconds to under one second and monthly database spend by approximately $2,000.',
          skills: ['Go', 'ClickHouse', 'PostgreSQL', 'TimescaleDB'],
        },
        {
          title: 'Waypoint APIs',
          description:
            'Built customer-facing APIs authenticated with API keys for PCF and tag-data ingestion, tag discovery, and historical data retrieval, with asynchronous ingestion queued through Redpanda. Designed batch-operation logic and implemented PCF flow and activity-data APIs, tag-data ingestion, and federation access. Later implemented tag discovery and retrieval of latest, raw, and aggregated datapoints, delivering outbound APIs to production.',
          skills: ['Go', 'Redpanda', 'API Design'],
        },
        {
          title: 'QuantumSurf Interoperability',
          description:
            'Led interoperability with QuantumSurf’s PCF data exchange. Authored technical and API specifications and worked directly with QuantumSurf engineering to deliver the integration.',
          skills: ['Go', 'API Design', 'PCF Interoperability'],
        },
        {
          title: 'OEE',
          description:
            'Helped build Overall Equipment Effectiveness tracking, including shift-based downtime, performance, and quality metrics. Led the downtime portion, normalized performance calculations using converted productive time, and moved Pareto-chart calculations to the backend to reduce client-side processing and improve reporting over large time ranges.',
          skills: ['Go', 'Time-Series Data', 'OEE'],
        },
        {
          title: 'Cofinity-X / Catena-X Interoperability',
          description:
            'Led technical design and implementation of interoperability between Glassdome’s PCF product and Cofinity-X’s data exchange. Built multi-step PCF exchange workflows using a Redpanda-backed saga to coordinate external calls. Worked directly with Cofinity-X engineers to resolve API ambiguities and improve integration documentation.',
          skills: ['Go', 'Redpanda', 'Cofinity-X', 'Catena-X'],
        },
        {
          title: 'Zitadel Migration',
          description:
            'Contributed to the implementation, maintenance, and delivery of the authentication-system migration from Kratos to Zitadel.',
          skills: ['Go', 'Kratos', 'Zitadel'],
        },
        {
          title: 'ACLs',
          description:
            'Led the design and implementation of access-control lists using SpiceDB, ensuring permissions propagated correctly without disrupting existing customers.',
          skills: ['Go', 'SpiceDB', 'Access Control'],
        },
        {
          title: 'PCF Emission-Activity Upload',
          description:
            'Built the original manual-ingestion workflow for customer PCF activity data. Implemented CSV/XLSX ingestion with custom schemas mapping source columns, units, categories, and directions. Added validation, row-level error reporting, upload templates, and upload history, and processed validated files into the pipeline for PCF calculations.',
          skills: ['Go', 'CSV / XLSX', 'Data Ingestion'],
        },
        {
          title: 'ecoinvent Database Upload',
          description:
            'Replaced a fixed calculation-factor dataset stored in a large static database migration with spreadsheet uploads, allowing new ecoinvent versions to be imported without code changes or migrations. Implemented company calculation-factor collections with a configured limit of 700 factors per company to support licensing requirements. Owned these features and adapted them to structural changes in later ecoinvent versions.',
          skills: ['Go', 'ecoinvent', 'Data Ingestion'],
        },
        {
          title: 'Siemens SiGREEN Integration',
          description:
            'Owned technical design and implementation of PCF interoperability between Glassdome and Siemens SiGREEN. Established the technical requirements and delivered the integration.',
          skills: ['Go', 'SiGREEN', 'PCF Interoperability'],
        },
      ],
    },
    {
      company: 'MXN Technology',
      title: 'Lead Software Engineer',
      dateRange: 'Sep 2021 - Oct 2024',
      description:
        'Seoul, South Korea. Led the internal R&D engineering team at an international logistics company, proposing and implementing new technologies. Consolidated infrastructure across teams from AWS, GCP, and Azure onto GCP, centralizing operations and enabling automated deployment pipelines. Led development of a Flutter-based beauty marketplace, establishing app foundations and owning TypeScript backend services and infrastructure designed for 300,000 daily users across Korea and the US. Designed order and warehouse management systems integrating Shopify, Naver SmartStore, and Coupang, and modernized Vue and JavaScript codebases to Vue 3 and TypeScript.',
      skills: [
        'TypeScript',
        'Node.js',
        'Vue',
        'Quasar',
        'Flutter / Dart',
        'Google Cloud',
        'PHP',
        'Laravel',
      ],
      projects: [
        {
          title: 'yless',
          description:
            'Led development of a beauty e-commerce app with a Dart/Flutter client and TypeScript backend deployed on AWS. Established the app foundations and trained remote contractors to take over client development, while designing, developing, and owning the server infrastructure and codebase. Designed the system to support 300,000 daily users across Korea and the US.',
          skills: ['Flutter / Dart', 'TypeScript', 'AWS'],
        },
        {
          title: 'Proveneer',
          description:
            'Rebranded MintCode for art galleries, rebuilding the client application while reusing much of the existing backend.',
          skills: [
            'JavaScript',
            'TypeScript',
            'Node.js',
            'Vue',
            'Quasar',
            'Flutter / Dart',
            'Google Cloud',
          ],
        },
        {
          title: 'MintCode',
          description:
            'Led development of an NFT provenance app with a Dart/Flutter client and TypeScript backend deployed on Google Cloud. The NFT infrastructure was designed externally; led development of the rest of the project.',
          skills: [
            'JavaScript',
            'TypeScript',
            'Node.js',
            'Flutter / Dart',
            'Google Cloud',
          ],
          externalLinks: [
            {
              url: 'https://mintcode.xyz/',
              text: 'MintCode website',
            },
          ],
        },
        {
          title: 'Customer Warehouse Management System',
          description:
            'Upgraded a client-specific inventory management webapp to Laravel 10 and PHP 8.2, rewriting substantial parts and adding type safety. Built with PHP and TypeScript and deployed on Google Cloud.',
          skills: ['PHP', 'Laravel', 'TypeScript', 'Google Cloud'],
        },
        {
          title: 'MintFulfillment Warehouse Management System',
          description:
            'Designed a warehouse management webapp and server from the ground up, enabling workers to manage inventory and fulfill orders. Used TypeScript on both frontend and backend, with a Vue/Quasar/Capacitor client.',
          skills: ['TypeScript', 'Node.js', 'Vue', 'Quasar', 'Capacitor'],
        },
        {
          title: 'MintFulfillment Order Management System',
          description:
            'Built an order management webapp and server connecting to Shopify, Naver SmartStore, and Coupang to import orders for warehouse fulfillment. Upgraded from Vue 2 to Vue 3 and converted the entire codebase from JavaScript to TypeScript.',
          skills: ['JavaScript', 'TypeScript', 'Node.js', 'Vue', 'Quasar'],
        },
      ],
    },
    {
      company: 'athenahealth',
      title: 'Senior Member of Technical Staff',
      dateRange: 'Aug 2017 - Jul 2021',
      description:
        'Watertown, MA, USA. Worked across Integration Services and Clinicals ePrescribing teams at an electronic medical record company. Contributed to the design, architecture, and implementation of e-prescribing modernization, replacing legacy workflows to support Surescripts’ NewSCRIPT standard. Served as long-term technical owner of a prescription-monitoring integration supporting approximately one million requests per day and reducing lookup time from 5–7 minutes to under 10 seconds. Migrated real-time prescription benefit checking from a Perl monolith to a Node.js microservice handling approximately six million requests per day. Served as Scrum Master for engineers based in the US and India.',
      skills: [
        'JavaScript',
        'AWS',
        'TypeScript',
        'Node.js',
        'Perl',
        'HTML / CSS',
      ],
      projects: [
        {
          title: 'ePrescribing Coupons',
          description:
            'Contributed to the technical design and initial implementation of a microservice retrieving coupons during the prescription flow, helping doctors find prices for their patients.',
          skills: ['TypeScript', 'AWS', 'Microservices'],
        },
        {
          title: 'NewSCRIPT',
          description:
            'Contributed to the design and implementation of the team’s upgrade to Surescripts’ new electronic-prescribing standard, rewriting substantial parts of the prescription workflow and replacing error-prone legacy logic. The broader ePrescribing team’s work was recognized when athenahealth achieved the highest accuracy score in e-prescribing quality in the 2020 Surescripts White Coat Award.',
          skills: ['JavaScript', 'Perl'],
          externalLinks: [
            {
              url: 'https://www.athenahealth.com/about/news/awards/athenahealth-wins-highest-accuracy-score-e-prescribing-quality-2020-surescripts-white-coat-award',
              text: 'athenahealth wins highest accuracy score in e-prescribing quality in 2020 Surescripts White Coat Award',
            },
          ],
        },
        {
          title: 'whoowns tool',
          description:
            'Built an internal developer tool at a hackathon to identify active contributors and owning teams for files in the monolith. Combined contribution history with ownership declarations to help engineers find relevant expertise.',
          skills: ['Developer Tooling'],
        },
        {
          title: 'Prescription Drug Monitoring Program',
          description:
            'Integrated state prescription-monitoring programs into the prescribing workflow using a Node.js microservice and React frontend, allowing doctors to review controlled-substance prescription histories without visiting separate state websites. Reduced lookup time from 5–7 minutes to under 10 seconds and supported approximately one million requests per day. Served as a long-term technical owner, trained new developers, and worked directly with doctors, vendors, and developers operating state systems.',
          skills: ['TypeScript', 'Node.js', 'React', 'AWS'],
        },
        {
          title: 'Real-Time Benefit Check',
          description:
            'Helped extract real-time prescription-benefit checking from the Perl monolith into a Node.js microservice, among the company’s first production microservices. Displayed drug prices and lower-cost alternatives within the prescribing workflow and supported approximately six million requests per day. Coordinated integrations with vendors selected according to patient insurance and helped establish AWS deployment and microservice practices.',
          skills: ['JavaScript', 'TypeScript', 'Node.js', 'Perl', 'AWS'],
          externalLinks: [
            {
              url: 'https://www.fiercehealthcare.com/payer/humana-athenahealth-team-to-embed-member-data-providers-ehr-workflows',
              text: 'Humana, athenahealth team to embed member data in providers\' EHR workflows',
            },
          ],
        },
      ],
    },
    {
      company: 'Thales Visionix',
      title: 'Associate Software Engineer',
      dateRange: 'Jul 2016 - Jul 2017',
      description:
        'Billerica, MA, USA. Developed software for motion trackers used in research, construction, and military applications. Designed and built a C# Unity plugin and demonstration application for trade shows. Owned the motion-tracker SDK, fixing embedded firmware issues, supporting legacy products, and updating the C++/Qt client and libraries for new product releases. Also provided technical support to customers.',
      skills: ['C', 'C++', 'C#', 'Qt', 'Unity'],
      projects: [
        {
          title: 'InterSense IS-1500 Unity Plugin',
          description:
            'Sole designer and developer of a C# Unity plugin integrating motion-tracker data. Built a demonstration mapping physical tracker movement to the virtual camera, showcased at conferences and demonstrated during two visits aboard a submarine under construction at Newport News Shipbuilding.',
          skills: ['C#', 'Unity'],
          externalLinks: [],
        },
        {
          title: 'InterSense Motion Tracker SDK',
          description:
            'Worked on the shared SDK for the company’s motion trackers, taking ownership of firmware bugs and upgrading the software client to support newer trackers. Used C for embedded firmware and C++ and Qt for the client.',
          skills: ['C', 'C++', 'Qt'],
          externalLinks: [
            {
              url: 'https://www.intersense.com/dev-tools',
              text: 'InterSense',
            },
          ],
        },
      ],
    },
  ]
</script>

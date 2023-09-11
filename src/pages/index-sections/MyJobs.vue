<template>
  <expandable-area icon-size="20px">
    <template #title> <span class="text-title">My Jobs</span></template>
    <div class="row q-col-gutter-sm">
      <template v-for="job in jobs" :key="job.company">
        <expandable-area class="col-12" icon-size="18px">
          <template #title>
            <span class="text-title-subsection q-pr-sm">
              {{ job.company }}
            </span>

            <span class="text-subtitle-subsection q-pr-sm">
              {{ job.title }}
            </span>

            <span
              class="text-subtitle-subsection"
              :style="{ fontStyle: 'italic' }"
            >
              {{ job.dateRange }}
            </span>
          </template>
          <div class="row q-col-gutter-sm">
            <div class="col-12">
              {{ job.description }}
            </div>
            <template v-for="skill in job.skills" :key="skill">
              <div class="col-auto">
                <q-chip class="skill-chip" dense :label="skill" />
              </div>
            </template>

            <div class="col-12">Projects</div>

            <div class="col-12 row q-col-gutter-md q-px-md">
              <template v-for="project in job.projects" :key="project.title">
                <expandable-area class="col-12" icon-size="14px">
                  <template #title>
                    <span class="text-title-subsubsection">
                      {{ project.title }}
                    </span>
                  </template>
                  <div class="row q-col-gutter-sm">
                    <template v-if="project.imageUrl">
                      <div class="col-4">
                        <q-img :src="project.imageUrl" />
                      </div>
                      <div class="col-8">
                        {{ project.description }}
                      </div>
                    </template>
                    <template v-else>
                      <div class="col-12">
                        {{ project.description }}
                      </div>
                    </template>
                    <template v-for="skill in project.skills" :key="skill">
                      <div class="col-auto">
                        <q-chip class="skill-chip" dense :label="skill" />
                      </div>
                    </template>
                  </div>
                </expandable-area>
              </template>
            </div>
          </div>
        </expandable-area>
      </template>
    </div>
  </expandable-area>
</template>

<script setup lang="ts">
import { faker } from '@faker-js/faker';

import ExpandableArea from 'components/ExpandableArea.vue';

type ExternalLink = {
  text: string;
  url: string;
};

type Project = {
  title: string;
  description: string;
  imageUrl?: string;
  skills: string[];
  externalLinks?: ExternalLink[];
};

type Job = {
  company: string;
  description: string;
  title: string;
  dateRange: string;
  imageUrl?: string;
  skills: string[];
  projects: Project[];
};

const jobs: Job[] = [
  {
    company: 'MXN Technology',
    title: 'Software Engineer',
    dateRange: 'Sep 2021 - Present',
    description:
      'Seoul, South Korea. MXN is an international logistics company, and I am an engineer on an R&D focused team, testing out technologies and projects new to the company. Lead effort to automate build pipelines; both within my direct team and helping other development teams. Worked with team to design and harden development practices towards a process that encouraged full participation of team members.',
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
        title: 'Proveneer',
        description:
          'Mobile app (built with Flutter) and webapp (built with Vue), with a Node.js server, for art galleries and collectors to track provenance of artworks.',
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
        title: 'Mintcode',
        description:
          'Mobile app (built with Flutter) with a Node.js server, for proving ownership history of collectibles. First time working with Flutter and Dart.',
        skills: [
          'JavaScript',
          'TypeScript',
          'Node.js',
          'Flutter / Dart',
          'Google Cloud',
        ],
      },
      {
        title: 'Warehouse Management System for an individual vendor',
        description:
          'Inventory management webapp specifically made for a client company. Upgraded an existing webapp to Laravel 10 and PHP 8.2, rewriting and adding type-safety to much of it in the process. First time working in PHP.',
        skills: ['PHP', 'Laravel', 'JavaScript', 'TypeScript', 'HTML'],
      },
      {
        title: 'Mintfulfillment Warehouse Management System',
        description:
          'Warehouse management webapp and server. Designed from the ground up. Workers can manage warehouse inventory and fulfill orders.',
        skills: ['TypeScript', 'Node.js', 'Vue', 'Quasar', 'Capacitor'],
      },
      {
        title: 'Mintfulfillment Order Management System',
        description:
          'Order management webapp and server. Connects with Shopify, Naver SmartStore, and Coupang to import orders, which can then be sent to a WMS to fulfill. Worked through upgrade from Vue 2 to Vue 3, and later conversion from JS to TypeScript.',
        skills: ['JavaScript', 'TypeScript', 'Node.js', 'Vue', 'Quasar'],
      },
    ],
  },
  {
    company: 'athenahealth',
    title: 'Senior Software Engineer',
    dateRange: 'Aug 2017 - Jun 2021',
    description:
      'Watertown, MA, USA. athenahealth creates an Electronic Medical Record (EMR) product, and I was on their Integration Services, and later, Clinicals teams. Our team built and maintained several RESTful microservices serving over 6 million requests per day. I was the subject matter expert on these services, and helped DevOps teams establish AWS best practices for the Clinicals engineering org, as well as the company at large. For some of this period I was the scrum master for a team spread across multiple timezones, and we still maintained productivity after switching to remote work with the outbreak of COVID.',
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
        title: 'NewSCRIPT',
        description:
          "Our team managed the upgrade to e-prescibing vendor Surescripts's new standard. This was a major change, rewriting much of our electronic prescription code, eliminating many dreaded bug factories along the way. This upgrade won athenahealth an award from Surescripts as one of the top ten companies in their network for prescription accuracy.",
        skills: ['JavaScript', 'Perl'],
        externalLinks: [
          {
            url: 'https://www.athenahealth.com/news/awards/athenahealth-wins-highest-accuracy-score-e-prescribing-quality-2020-surescripts-white-coat-award',
            text: 'athenahealth wins highest accuracy score in e-prescribing quality in 2020 Surescripts White Coat Award',
          },
        ],
      },
      {
        title: 'Prescription Drug Monitoring Program',
        description:
          "Connects with state prescription monitoring programs to enable doctors to view patients' controlled drug history (required by law in most states) without leaving the prescription workflow. Before this, they had to go through the states' sites individually, taking 5-7 minutes, while our process took less than 10 seconds. The Node.js microservice supporting this took in millions of requests per day and scaled stably. I often interacted directly with vendors and developers on the states' systems as part of this project.",
        skills: ['JavaScript', 'TypeScript', 'Node.js', 'Perl', 'AWS'],
        externalLinks: [
          {
            url: 'https://www.athenahealth.com/knowledge-hub/clinical-trends/3-minute-case-study-smart-seamless-opioid-prescribing',
            text: '3-minute case study: Smart, seamless opioid prescribing',
          },
        ],
      },
    ],
  },
];

for (let i = 0; i < 5; i++) {
  const newJob: Job = {
    company: 'Company ' + i,
    title: 'Job Title ' + i,
    dateRange: 'Aug 1994 - Aug 1995',
    description: faker.lorem.paragraphs(),
    skills: [
      'JavaScript',
      'TypeScript',
      'Node.js',
      'Vue',
      'Quasar',
      'Flutter / Dart',
      'Google Cloud',
      'PHP',
      'Laravel',
    ],
    projects: [],
  };

  for (let i = 0; i < 3; i++) {
    newJob.projects.push({
      title: 'Project ' + i,
      description: faker.lorem.paragraphs(),
      skills: [
        'JavaScript',
        'TypeScript',
        'Node.js',
        'Vue',
        'Quasar',
        'Flutter / Dart',
        'Google Cloud',
        'PHP',
        'Laravel',
      ],
      imageUrl: Math.random() > 0.75 ? faker.image.url() : undefined,
    });
  }
  jobs.push(newJob);
}
</script>

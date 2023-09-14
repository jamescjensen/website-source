<template>
  <expandable-area icon-size="20px">
    <template #title> <span class="text-title">Job History</span></template>
    <div class="row q-col-gutter-sm">
      <template v-for="(job, index) in jobs" :key="job.company">
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

            <template v-if="job.projects.length">
              <expandable-area class="col-12 q-px-md" :initial-expanded="false">
                <template #title> Projects </template>

                <div class="col-12 row q-col-gutter-md">
                  <template
                    v-for="project in job.projects"
                    :key="project.title"
                  >
                    <div class="col-xs-12 col-sm-4">
                      <project-card :project="project" />
                    </div>
                  </template>
                </div>
              </expandable-area>
            </template>
          </div>
          <template v-if="index !== jobs.length - 1">
            <q-separator class="q-ma-md" />
          </template>
        </expandable-area>
      </template>
    </div>
  </expandable-area>
</template>

<script setup lang="ts">
import ProjectCard, { type Project } from './ProjectCard.vue';
import ExpandableArea from 'components/ExpandableArea.vue';

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
        externalLinks: [
          {
            url: 'https://mintcode.xyz',
            text: 'Mintcode website',
          },
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
      {
        title: 'Real-Time Benefit Check',
        description:
          "Shows doctors drug prices as part of their prescribing workflow, as well as cheaper alternatives. The microservice supporting this took 6 million requests on an average day, and scaled smoothly to support this through the day. This service goes out to several different vendors based on the patient's insurance, and supporting this project involved meeting with those vendors regularly. This service was also originally written in athenahealth's Perl monolith, but was successfully broken out into a Node.js microservice, one of the first microservices in the company to go GA.",
        skills: ['JavaScript', 'TypeScript', 'Node.js', 'Perl', 'AWS'],
        externalLinks: [
          {
            url: 'https://www.fiercehealthcare.com/payer/humana-athenahealth-team-to-embed-member-data-providers-ehr-workflows',
            text: "Humana, athenahealth team to embed member data in providers' EHR workflows",
          },
        ],
      },
    ],
  },
  {
    company: 'Thales Visionix (now Thales InterSense)',
    title: 'Associate Software Engineer',
    dateRange: 'Jul 2016 - Jul 2017',
    description:
      'Billerica, MA, USA. Our division of Thales Visionix focused on motion trackers, and I was a generalist developer on software to support them, as well as doing customer service for researchers using them.',
    skills: ['C', 'C++', 'C#', 'Qt', 'Unity'],
    projects: [
      {
        title: 'Unity Plugin',
        description:
          'I was the sole developer on a plugin for the Unity 3D engine, retrieving data from the tracker to, for example, move the camera in-engine. This also involved building a demo that was showcased at several conferences and visiting one client site to help them test the tracker.',
        skills: ['C#', 'Unity'],
        externalLinks: [],
      },
      {
        title: 'Tracker SDK',
        description:
          "I worked on the shared SDK for all of the company's trackers, taking ownership of and fixing bugs in the firmware, and upgrading the software used to display data to support more recent trackers.",
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
];
</script>

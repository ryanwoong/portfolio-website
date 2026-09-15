<script setup>
import AwsIcon from "~icons/logos/aws";
import AzureIcon from "~icons/logos/azure-icon";
import CSharpIcon from "~icons/logos/c-sharp";
import ClaudeIcon from "~icons/logos/claude-icon";
import DockerIcon from "~icons/logos/docker-icon";
import DotNetIcon from "~icons/logos/dotnet";
import ElectronIcon from "~icons/logos/electron";
import ExpressIcon from "~icons/logos/express";
import FastApiIcon from "~icons/logos/fastapi-icon";
import FirebaseIcon from "~icons/logos/firebase";
import GitHubIcon from "~icons/logos/github-icon";
import HtmlIcon from "~icons/logos/html-5";
import JavaIcon from "~icons/logos/java";
import JavaScriptIcon from "~icons/logos/javascript";
import KotlinIcon from "~icons/logos/kotlin-icon";
import LinuxIcon from "~icons/logos/linux-tux";
import MongoDbIcon from "~icons/logos/mongodb-icon";
import NodeIcon from "~icons/logos/nodejs-icon";
import OllamaIcon from "~icons/simple-icons/ollama";
import OpenAiIcon from "~icons/logos/openai-icon";
import PostgreSqlIcon from "~icons/logos/postgresql";
import PythonIcon from "~icons/logos/python";
import ReactIcon from "~icons/logos/react";
import SqlIcon from "~icons/logos/sqlite";
import TypeScriptIcon from "~icons/logos/typescript-icon";
import VllmIcon from "~icons/simple-icons/vllm";
import VueIcon from "~icons/logos/vue";

const props = defineProps({ name: String });

const icons = {
  "C#": CSharpIcon,
  "HTML / CSS": HtmlIcon,
  Java: JavaIcon,
  JavaScript: JavaScriptIcon,
  Kotlin: KotlinIcon,
  Python: PythonIcon,
  SQL: SqlIcon,
  TypeScript: TypeScriptIcon,
  ".NET": DotNetIcon,
  Electron: ElectronIcon,
  "Express.js": ExpressIcon,
  FastAPI: FastApiIcon,
  "Node.js": NodeIcon,
  React: ReactIcon,
  Vue: VueIcon,
  AWS: AwsIcon,
  Azure: AzureIcon,
  "Claude Code": ClaudeIcon,
  Docker: DockerIcon,
  "Git/GitHub": GitHubIcon,
  Linux: LinuxIcon,
  OpenAI: OpenAiIcon,
  Ollama: OllamaIcon,
  Unsloth: "pi pi-bolt",
  vLLM: VllmIcon,
  Firebase: FirebaseIcon,
  MongoDB: MongoDbIcon,
  PostgreSQL: PostgreSqlIcon,
};
</script>

<template>
  <span class="tag skill-tag">
    <component
      v-if="typeof icons[name] !== 'string'"
      class="skill-icon"
      :is="icons[name]"
      aria-hidden="true"
    />
    <i
      v-else
      :class="icons[name]"
      aria-hidden="true"
    />
    {{ name }}
  </span>
</template>

<style scoped>
.skill-tag {
  display: inline-flex;
  align-items: center;
  gap: 0.42rem;
}

.skill-icon,
.skill-tag > .pi {
  width: 1rem;
  height: 1rem;
  flex: 0 0 auto;
}

.skill-tag > .pi {
  color: var(--primary-strong);
  font-size: 0.9rem;
}
</style>

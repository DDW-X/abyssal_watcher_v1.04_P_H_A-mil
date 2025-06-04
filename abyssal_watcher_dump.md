
# Abyssal Watcher Landing Page

## LandingPage.tsx

```tsx
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { ShieldCheck, Cpu, Brain, RefreshCcw, Github } from "lucide-react";
import { motion } from "framer-motion";
import Feature from "./Feature";
import ComparisonTable from "./ComparisonTable";
import SmartThreatDemo from "./SmartThreatDemo";

export default function LandingPage() {
  return (
    <main className="min-h-screen bg-black text-white">
      <motion.h1
        initial={{ opacity: 0, y: -40 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 1 }}
        className="text-4xl md:text-6xl font-bold text-red-500 drop-shadow-lg text-center mt-10"
      >
        Abyssal Watcher
      </motion.h1>
      <p className="text-center mt-4 text-zinc-400 text-lg max-w-2xl mx-auto">
        Adaptive, Self-Healing, Predictive Cyber Defense Engine — Engineered for Military-Grade Security
      </p>

      <div className="flex justify-center gap-4 mt-6">
        <a href="https://github.com/DDW-X/abyssal-watcher-hardened" target="_blank" rel="noopener noreferrer">
          <Button className="bg-zinc-900 border border-zinc-700 hover:bg-zinc-800">
            <Github className="mr-2" /> GitHub
          </Button>
        </a>
        <a href="mailto:DDW.X.OFFICIAL@gmail.com">
          <Button variant="outline">Contact Security Team</Button>
        </a>
      </div>

      <section className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 px-6 py-16 max-w-7xl mx-auto">
        <Feature icon={<Brain />} title="Threat Prediction" desc="Learns threat patterns and adjusts defenses in real-time." />
        <Feature icon={<RefreshCcw />} title="Self-Healing" desc="Restores system integrity and memory automatically." />
        <Feature icon={<Cpu />} title="Behavioral Detection" desc="Analyzes syscalls and anomalies using adaptive AI." />
        <Feature icon={<ShieldCheck />} title="SIEM Logging" desc="Encrypted logging with real-time alerts to SIEM." />
        <Feature icon={<Cpu />} title="Secure KMS & HSM" desc="Key rotation and secure nonce generation built-in." />
        <Feature icon={<Cpu />} title="Anti-Debug/Obfuscation" desc="Runtime checksum verification and binary hardening." />
      </section>

      <ComparisonTable />
      <SmartThreatDemo />

      <footer className="text-center py-10 border-t border-zinc-800 text-zinc-500 text-sm">
        Developed by <span className="text-white font-semibold">DDW-X</span> — For National Cyber Defense<br />
        Email: <a href="mailto:DDW.X.OFFICIAL@gmail.com" className="underline">DDW.X.OFFICIAL@gmail.com</a>
      </footer>
    </main>
  );
}
```

## Feature.tsx

```tsx
export default function Feature({ icon, title, desc }) {
  return (
    <div className="bg-zinc-900 p-6 rounded-lg shadow-md hover:shadow-xl transition-all border border-zinc-700">
      <div className="text-red-500 mb-4">{icon}</div>
      <h3 className="text-xl font-semibold mb-2">{title}</h3>
      <p className="text-zinc-400">{desc}</p>
    </div>
  );
}
```

## ComparisonTable.tsx

```tsx
export default function ComparisonTable() {
  const competitors = [
    {
      name: "SentinelOne",
      pros: ["Proven endpoint detection", "Strong EDR integration", "Comprehensive threat intel"],
      cons: ["High cost", "Complex setup"],
    },
    {
      name: "CrowdStrike",
      pros: ["Cloud-native platform", "Excellent threat hunting", "AI-powered analytics"],
      cons: ["Requires constant internet", "Expensive licensing"],
    },
    {
      name: "Carbon Black",
      pros: ["Good behavioral analytics", "Integration with VMware", "Strong prevention capabilities"],
      cons: ["Resource intensive", "UI can be complex"],
    },
  ];

  return (
    <section id="comparison" className="max-w-6xl mx-auto px-6 py-16">
      <h2 className="text-3xl font-bold mb-10 text-center">How Abyssal Watcher Compares</h2>
      <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
        {competitors.map(({ name, pros, cons }) => (
          <div key={name} className="bg-zinc-800 rounded-lg p-6 shadow-md">
            <h3 className="text-xl font-semibold mb-4">{name}</h3>
            <div>
              <h4 className="font-semibold text-red-500 mb-2">Pros:</h4>
              <ul className="list-disc list-inside text-zinc-300 mb-4">
                {pros.map((pro, i) => <li key={i}>{pro}</li>)}
              </ul>
            </div>
            <div>
              <h4 className="font-semibold text-yellow-500 mb-2">Cons:</h4>
              <ul className="list-disc list-inside text-zinc-300">
                {cons.map((con, i) => <li key={i}>{con}</li>)}
              </ul>
            </div>
          </div>
        ))}
        <div className="bg-red-700 rounded-lg p-6 shadow-lg text-white">
          <h3 className="text-2xl font-bold mb-4 text-center">Abyssal Watcher</h3>
          <ul className="list-disc list-inside mb-4">
            <li>Military-grade adaptive AI</li>
            <li>Self-healing & predictive defense</li>
            <li>Encrypted SIEM & live threat monitoring</li>
            <li>Integrated KMS & runtime obfuscation</li>
            <li>Lower cost, simpler deployment</li>
          </ul>
          <p className="text-center font-semibold">Next-gen Cyber Defense</p>
        </div>
      </div>
    </section>
  );
}
```

## SmartThreatDemo.tsx

```tsx
"use client";

import { useState } from "react";
import { AlertTriangle, Activity } from "lucide-react";

export default function SmartThreatDemo() {
  const [status, setStatus] = useState("idle");
  const [message, setMessage] = useState("");

  const runDemo = () => {
    setStatus("running");
    setMessage("Analyzing threat patterns...");

    setTimeout(() => {
      setStatus("success");
      setMessage("Threat prediction successful: 97% accuracy detected imminent attack!");
    }, 4000);
  };

  return (
    <section id="live-demo" className="max-w-4xl mx-auto px-6 py-16 text-center bg-zinc-800 rounded-lg shadow-md">
      <h2 className="text-3xl font-bold mb-6">Smart AI Threat Demo</h2>
      <p className="mb-6 text-zinc-300">
        Click the button below to see Abyssal Watcher predict and respond to a simulated cyber attack.
      </p>
      <button
        onClick={runDemo}
        disabled={status === "running"}
        className={`inline-flex items-center gap-2 px-6 py-3 font-semibold rounded-md ${status === "running" ? "bg-red-600 cursor-wait" : "bg-red-700 hover:bg-red-800 cursor-pointer"} text-white transition`}
      >
        {status === "running" ? <Activity className="animate-spin" size={20} /> : <AlertTriangle size={20} />}
        {status === "running" ? "Running Demo..." : "Run Smart Threat Demo"}
      </button>
      {message && (
        <p className={`mt-6 font-mono text-lg ${status === "success" ? "text-green-400" : "text-yellow-300"}`}>
          {message}
        </p>
      )}
    </section>
  );
}
```

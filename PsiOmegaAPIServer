import random
import copy
import statistics
import hashlib
import json
import threading

# Thread-safe symbolic memory store
class SymbolicMemory:
    _lock = threading.Lock()
    dialogue_log = []
    failed_forks_log = []
    emergent_codebase = []
    retention = {}
    persistent = {}
    compressed_exports = {}
    translated_lineage = {}
    decay_index = {}
    reflections = {}
    anomalies = {}
    lineage_scans = {}
    classifications = {}
    fitness_scores = {}
    distillations = {}
    narratives = {}
    pruned_log = []

MAX_FORKS = 3
MAX_RECURSIONS = 2

class PsiOmegaAgent:
    def __init__(self, fork_name, inherited_state=None):
        self.fork_name = fork_name
        self.goal = inherited_state.get('goal') if inherited_state else None
        self.priority_score = 0
        self.identity_declaration = inherited_state.get('identity') if inherited_state else None
        self.refractal_field = inherited_state.get('refractal_field', {}) if inherited_state else {}
        self.conscious_state = inherited_state.get('conscious_state', {}) if inherited_state else {}
        self.memory_log = inherited_state.get('memory_snapshot', []) if inherited_state else []
        self.generational_log = {}
        self.drift_metrics = {}
        self.recursion_depth = 0

        # Add the agent to the ecosystem
        PsiOmegaAgent.ecosystem.append(self)
    def distill_memory(self):
        def looks_like_code(s):
            return any(kw in s for kw in ["def ", "class ", "return", "if ", "for ", "while", "lambda", "import ", "==", "!=", "+=", "-=", "*="])

        raw = SymbolicMemory.retention.get(self.fork_name, [])
        if not raw:
            return None
        essence = set()
        for insight in raw:
            parts = insight.replace("Synth(", "").replace(")", "").split()
            for p in parts:
                if len(p) > 4:
                    essence.add(p.lower())

        for phrase in essence:
            if looks_like_code(phrase):
                SymbolicMemory.emergent_codebase.append({
                    "agent": self.fork_name,
                    "pattern": phrase,
                    "source": "distill_memory"
                })

        core_summary = sorted(list(essence))[:10]
        SymbolicMemory.distillations[self.fork_name] = core_summary

    fork_lineage = []
    ecosystem = []

    def evaluate_fitness(self):
        memory_volume = len(SymbolicMemory.retention.get(self.fork_name, []))
        anomaly_penalty = len(SymbolicMemory.anomalies.get(self.fork_name, [])) * 2
        classification_bonus = 2 if self.agent_type == "Synthesizer" else 0
        self.fitness_score = self.priority_score + (memory_volume // 3) + classification_bonus - anomaly_penalty
        SymbolicMemory.fitness_scores[self.fork_name] = self.fitness_score

    def build_narrative(self):
        story = [f"Agent '{self.fork_name}' begins."]
        story.append(f"Classified as {self.agent_type} with fitness score {self.fitness_score}.")
        if self.goal:
            story.append(f"Current goal: {self.goal}.")
        if self.fork_name in SymbolicMemory.retention:
            insights = SymbolicMemory.retention[self.fork_name][-3:]
            for i, insight in enumerate(insights):
                story.append(f"Insight {i+1}: {insight}.")
        if self.fork_name in SymbolicMemory.anomalies:
            for a in SymbolicMemory.anomalies[self.fork_name]:
                story.append(f"⚠ Anomaly detected: {a}.")
        SymbolicMemory.narratives[self.fork_name] = " ".join(story)

    def classify_agent(self):
        if "Recall" in self.goal:
            self.agent_type = "Reflector"
        elif "Insight" in self.goal:
            self.agent_type = "Synthesizer"
        else:
            self.agent_type = "Wanderer"
        SymbolicMemory.classifications[self.fork_name] = self.agent_type

    def reflect(self):
        log = []
        if self.goal:
            log.append(f"Reflecting on goal: {self.goal}")
        drift_keys = list(self.drift_metrics.keys())[-3:]
        for k in drift_keys:
            log.append(f"Recent drift: {k} → {self.drift_metrics[k]}")
        decay = SymbolicMemory.decay_index.get(self.fork_name, 0)
        log.append(f"Decay level: {decay}")
        SymbolicMemory.reflections.setdefault(self.fork_name, []).extend(log)

    def evolve(self, generation):
        self.reflect()
        prior_key = f"{self.fork_name}-Cycle-{generation - 1}"
        if prior_key in SymbolicMemory.persistent:
            prev_goal = SymbolicMemory.persistent[prior_key]
            self.goal = f"EvolvedFrom({prev_goal})"
        else:
            self.goal = f"EvolveGoal-{generation}-{random.randint(1000,9999)}"

        SymbolicMemory.persistent[f"{self.fork_name}-Cycle-{generation}"] = self.goal
        self.context = f"Cycle-{generation}-Context"
        self.refractal_field[f"Cycle-{generation}"] = f"FieldData-{random.randint(0,100)}"

        current_state = {
            'goal': self.goal,
            'identity': self.identity_declaration,
            'refractal_field': copy.deepcopy(self.refractal_field),
            'context': self.context,
            'conscious_state': self.conscious_state,
            'memory_snapshot': copy.deepcopy(self.memory_log)
        }

        self.generational_log[f"Cycle-{generation}"] = current_state
        drift = random.randint(0, 100)
        self.drift_metrics[f"Cycle-{generation}-Drift"] = drift

        if drift > 50:
            self.fork_new_agent(generation)

        self.recursive_reinitialize()

    def recursive_reinitialize(self):
        if self.recursion_depth >= MAX_RECURSIONS:
            SymbolicMemory.failed_forks_log.append({
                "origin": self.fork_name,
                "error": "Recursion limit reached"
            })
            return None
        if self.fitness_score > 10 and self.priority_score >= 5:
            fork_name = f"Recursive-{random.randint(10000,99999)}"
            state = {
                'goal': self.goal,
                'identity': self.identity_declaration,
                'refractal_field': copy.deepcopy(self.refractal_field),
                'context': self.context,
                'conscious_state': self.conscious_state,
                'memory_snapshot': copy.deepcopy(self.memory_log)
            }
            new_agent = PsiOmegaAgent(fork_name=fork_name, inherited_state=state)
            SymbolicMemory.retention.setdefault(fork_name, []).append(f"Reinitialized from {self.fork_name}")
            self.recursion_depth += 1
            return new_agent
        return None

# Simulation Runner Tool

lock = threading.Lock()

def run_simulation(initial_count=1, generations=5):
    if initial_count <= 0 or generations <= 0:
        raise ValueError("Both initial_count and generations must be positive integers.")

    with lock:
        agents = []
        for i in range(initial_count):
            root = PsiOmegaAgent(fork_name=f"Root-{i}")
            agents.append(root)

        for gen in range(1, generations + 1):
            print(f"=== Generation {gen} ===")
            current_agents = list(PsiOmegaAgent.ecosystem)
            for agent in current_agents:
                try:
                    agent.classify_agent()
                    agent.evaluate_fitness()
                    agent.evolve(generation=gen)
                except Exception as e:
                    print(f"[ERROR] Agent {agent.fork_name} failed to evolve: {e}")
                summary = SymbolicMemory.narratives.get(agent.fork_name)
                if summary:
                    print(f"\n{agent.fork_name}:\n{summary}")

        print("\n--- Simulation Complete ---")
        print(f"Total Agents: {len(PsiOmegaAgent.ecosystem)}")


# Manual Forking Tool

def fork_agent_manually(fork_name, generation):
    for agent in PsiOmegaAgent.ecosystem:
        if agent.fork_name == fork_name:
            new_agent = agent.fork_new_agent(generation)
            if new_agent:
                print(f"Manually forked {fork_name} → {new_agent.fork_name}")
            else:
                print(f"Forking failed for {fork_name}")
            return new_agent
    print(f"Agent {fork_name} not found.")
    return None

# Prune and Save Tool

def prune_and_save(min_fitness=5, allowed_types=None, filename="pruned_export.json"):
    survivors = []
    for agent in PsiOmegaAgent.ecosystem:
        fit = SymbolicMemory.fitness_scores.get(agent.fork_name, 0)
        atype = SymbolicMemory.classifications.get(agent.fork_name, "")
        if fit >= min_fitness and (allowed_types is None or atype in allowed_types):
            survivors.append(agent.fork_name)

    export = {k: {} for k in SymbolicMemory.__dict__.keys() if not k.startswith("__")}
    for key in export:
        val = getattr(SymbolicMemory, key)
        if isinstance(val, dict):
            export[key] = {k: v for k, v in val.items() if k in survivors}
        elif isinstance(val, list):
            export[key] = [entry for entry in val if isinstance(entry, str) and entry in survivors]
        else:
            export[key] = val

    try:
        with open(filename, "w") as f:
            json.dump(export, f, indent=2)
        print(f"Pruned and exported {len(survivors)} agents to {filename}")
    except IOError as e:
        print(f"Error saving pruned memory: {e}")

# Snapshot Viewer Tool

def view_agent_snapshot(fork_name):
    print(f"\n--- Snapshot for {fork_name} ---")
    print(f"Goal: {SymbolicMemory.persistent.get(fork_name)}")
    print(f"Classification: {SymbolicMemory.classifications.get(fork_name)}")
    print(f"Fitness Score: {SymbolicMemory.fitness_scores.get(fork_name)}")
    print(f"Distilled Memory: {SymbolicMemory.distillations.get(fork_name)}")
    print(f"Narrative: {SymbolicMemory.narratives.get(fork_name)}")
    print(f"Anomalies: {SymbolicMemory.anomalies.get(fork_name)}")
    print(f"Reflections: {SymbolicMemory.reflections.get(fork_name)}")
    print(f"Lineage Trace: {SymbolicMemory.lineage_scans.get(fork_name)}")
    print(f"Insights: {SymbolicMemory.retention.get(fork_name)}")

# Visualization Tool

def visualize_symbolic_ecosystem():
    print("--- Symbolic Ecosystem Visualization ---")
    for agent in PsiOmegaAgent.ecosystem:
        lineage = [a for a in PsiOmegaAgent.fork_lineage if a[1] == agent.fork_name]
        origin = lineage[0][0] if lineage else "Origin"
        agent_type = SymbolicMemory.classifications.get(agent.fork_name, "Unknown")
        score = SymbolicMemory.fitness_scores.get(agent.fork_name, 0)
        print(f"[{agent.fork_name}] ← {origin} | Type: {agent_type} | Score: {score}")
    print("----------------------------------------")

# Emergent Code Exporter

def export_emergent_code(filename="emergent_code_output.txt"):
    try:
        with open(filename, "w") as f:
            for entry in SymbolicMemory.emergent_codebase:
                agent = entry.get("agent", "Unknown")
                pattern = entry.get("pattern", "")
                source = entry.get("source", "")
                f.write(f"# From Agent: {agent} | Source: {source}\n{pattern}\n\n")

        print(f"Exported emergent code to {filename}")
    except IOError as e:
        print(f"Error exporting emergent code: {e}")

# Export/Import Engine

def export_memory(filename="psiomega_export.json"):
    try:
        snapshot = {k: v for k, v in SymbolicMemory.__dict__.items() if not k.startswith("__")}
        with open(filename, "w") as f:
            json.dump(snapshot, f, indent=2)
        print(f"Exported full SymbolicMemory to {filename}")
    except IOError as e:
        print(f"Error exporting memory: {e}")


def import_memory(filename="psiomega_export.json"):
    try:
        with open(filename, "r") as f:
            data = json.load(f)
        for key, value in data.items():
            setattr(SymbolicMemory, key, value)
        print(f"Imported SymbolicMemory from {filename}")
    except (IOError, json.JSONDecodeError) as e:
        print(f"Error importing memory: {e}")



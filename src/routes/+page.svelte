<script lang="ts">
    let projects: string[] = ["Project Alpha", "Project Beta", "Project Gamma"];
    let selectedProject: string = "";

    class BadgeSet {
        [key: string]: string | null;
    
        constructor() {
            this["Creativity & Innovation"] = null;
            this["Technical Mastery"] = null;
            this["Community Impact"] = null;
            this["User Experience"] = null;
            this["Quality & Completeness"] = null;
        }
    }

    // Use the BadgeSet class to simplify badge creation
    let badges: BadgeSet = new BadgeSet();

    let projectBadges: Record<string, BadgeSet> = {
    "Project Alpha": new BadgeSet(),
    "Project Beta": new BadgeSet(),
    "Project Gamma": new BadgeSet()
    };
  
    let badgeTiers: string[] = ["Explorer", "Innovator", "Pioneer", "Visionary"];
  
    // Map badge tiers to both primary and pale colors with corresponding thin outlines
    let tierColors: Record<string, { primary: string; pale: string; outline: string }> = {
      Explorer: { primary: "bg-amber-700", pale: "bg-gray-100", outline: "border-amber-700" },  // Bronze
      Innovator: { primary: "bg-gray-400", pale: "bg-gray-100", outline: "border-gray-400" },   // Silver
      Pioneer: { primary: "bg-yellow-500", pale: "bg-gray-100", outline: "border-yellow-500" }, // Gold
      Visionary: { primary: "bg-blue-300", pale: "bg-gray-100", outline: "border-blue-300" }    // Diamond
    };
  
    function awardBadge(category: string, tier: string) {
      if (selectedProject) {
        badges[category] = tier;
        projectBadges[selectedProject][category] = tier;
      }
    }
  
    function selectProject(project: string) {
      selectedProject = project;
      badges = { ...projectBadges[project] };
    }
  </script>
  
  <div class="min-h-screen p-6 bg-blue-100">
    <h1 class="text-3xl font-bold text-center mb-8">ACT Students' Digital Innovations Showcase</h1>
    <h2 class="text-2xl text-center font-bold mb-4">Project Awards</h2>
  
    <div class="flex justify-center mb-8">
      <select class="p-2 rounded bg-white shadow" bind:value={selectedProject} on:change={() => selectProject(selectedProject)}>
        <option value="" disabled selected>Select a Project</option>
        {#each projects as project}
          <option value={project}>{project}</option>
        {/each}
      </select>
    </div>
  
    {#if selectedProject}
      <div class="bg-white p-6 rounded shadow-md max-w-md mx-auto">
        <h2 class="text-2xl font-semibold mb-4">Award Badges for {selectedProject}</h2>
  
        <div class="space-y-4">
          {#each Object.keys(badges) as category}
            <div>
              <h3 class="font-medium text-lg">{category}</h3>
              <div class="flex space-x-2 mt-2">
                {#each badgeTiers as tier}
                  <button
                    class={`px-4 py-2 rounded-full ${
                      badges[category] === tier
                        ? `${tierColors[tier].primary} text-black font-semibold border border-black`
                        : `${tierColors[tier].pale} text-gray-700 border ${tierColors[tier].outline}`
                    }`}
                    on:click={() => awardBadge(category, tier)}
                  >
                    {tier}
                  </button>
                {/each}
              </div>
            </div>
          {/each}
        </div>
      </div>
    {/if}
  </div>
  
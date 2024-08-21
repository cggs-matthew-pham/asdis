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
  
    class TechnicalBadgeSet {
      [key: string]: boolean;
  
      constructor() {
        // Digital Media
        this["Digital Art Dynamo"] = false;
        this["Video Virtuoso"] = false;
        this["Animation Ace"] = false;
        this["Interactive Media Innovator"] = false;
  
        // Software Development
        this["Web Development Wizard"] = false;
        this["Mobile App Maven"] = false;
        this["Game Development Guru"] = false;
        this["Software Tool Specialist"] = false;
  
        // Data Science
        this["Data Visualization Virtuoso"] = false;
        this["Machine Learning Maverick"] = false;
        this["Predictive Analytics Pioneer"] = false;
        this["Data Analysis Ace"] = false;
  
        // Networking & Security
        this["System Admin Ace"] = false;
        this["Cybersecurity Guardian"] = false;
        this["Ethical Hacker Hero"] = false;
        this["Network Architect"] = false;
  
        // Robotics & Mechatronics
        this["Robotics Engineer Extraordinaire"] = false;
        this["Automation Specialist"] = false;
        this["Mechatronics Integrator"] = false;
        this["IoT Innovator"] = false;
        this["Smart Device Specialist"] = false;
  
        // AI & Machine Learning
        this["AI Architect"] = false;
        this["Neural Network Navigator"] = false;
        this["Intelligent Automation Innovator"] = false;
        this["Machine Learning Maverick"] = false;
      }
    }
  
    let badges: BadgeSet = new BadgeSet();
  
    let projectBadges: Record<string, { projectBadges: BadgeSet; technicalBadges: TechnicalBadgeSet }> = {
      "Project Alpha": { projectBadges: new BadgeSet(), technicalBadges: new TechnicalBadgeSet() },
      "Project Beta": { projectBadges: new BadgeSet(), technicalBadges: new TechnicalBadgeSet() },
      "Project Gamma": { projectBadges: new BadgeSet(), technicalBadges: new TechnicalBadgeSet() }
    };
  
    let badgeTiers: string[] = ["Explorer", "Innovator", "Pioneer", "Visionary"];
  
    let tierColors: Record<string, { primary: string; pale: string; outline: string }> = {
      Explorer: { primary: "bg-amber-700", pale: "bg-gray-100", outline: "border-amber-700" },  // Bronze
      Innovator: { primary: "bg-gray-400", pale: "bg-gray-100", outline: "border-gray-400" },   // Silver
      Pioneer: { primary: "bg-yellow-500", pale: "bg-gray-100", outline: "border-yellow-500" }, // Gold
      Visionary: { primary: "bg-blue-300", pale: "bg-gray-100", outline: "border-blue-300" }    // Diamond
    };
  
    function awardProjectBadge(category: string, tier: string) {
      if (selectedProject) {
        projectBadges[selectedProject].projectBadges[category] = tier;
      }
    }
  
    function toggleTechnicalBadge(technicalBadge: string) {
      if (selectedProject) {
        projectBadges[selectedProject].technicalBadges[technicalBadge] = !projectBadges[selectedProject].technicalBadges[technicalBadge];
      }
    }
  
    function selectProject(project: string) {
      selectedProject = project;
      badges = { ...projectBadges[project].projectBadges };
    }
  </script>
  
  <div class="min-h-screen p-6 bg-cyan-100">
    <h1 class="text-3xl font-bold text-center mb-8">ACT Students' Digital Innovations Showcase</h1>
    <h2 class="text-2xl text-center font-bold mb-4">Technical Achievements</h2>

  
    <div class="flex justify-center mb-8">
      <select class="p-2 rounded bg-white shadow" bind:value={selectedProject} on:change={() => selectProject(selectedProject)}>
        <option value="" disabled selected>Select a Project</option>
        {#each projects as project}
          <option value={project}>{project}</option>
        {/each}
      </select>
    </div>
  
    {#if selectedProject}
      <div class="flex flex-col items-center">
        <h2 class="text-2xl font-semibold mb-4">Award Badges for {selectedProject}</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-screen-lg">
          <!-- Digital Media -->
          <div>
            <h3 class="font-semibold text-lg mb-2">Digital Media</h3>
            {#each ["Digital Art Dynamo", "Video Virtuoso", "Animation Ace", "Interactive Media Innovator"] as techBadge}
              <div class="flex items-center space-x-2">
                <input type="checkbox" id={techBadge} checked={projectBadges[selectedProject]?.technicalBadges[techBadge]} on:change={() => toggleTechnicalBadge(techBadge)} />
                <label for={techBadge} class="text-lg">{techBadge}</label>
              </div>
            {/each}
          </div>
  
          <!-- Software Development -->
          <div>
            <h3 class="font-semibold text-lg mb-2">Software Development</h3>
            {#each ["Web Development Wizard", "Mobile App Maven", "Game Development Guru", "Software Tool Specialist"] as techBadge}
              <div class="flex items-center space-x-2">
                <input type="checkbox" id={techBadge} checked={projectBadges[selectedProject]?.technicalBadges[techBadge]} on:change={() => toggleTechnicalBadge(techBadge)} />
                <label for={techBadge} class="text-lg">{techBadge}</label>
              </div>
            {/each}
          </div>
  
          <!-- Data Science -->
          <div>
            <h3 class="font-semibold text-lg mb-2">Data Science</h3>
            {#each ["Data Visualization Virtuoso", "Machine Learning Maverick", "Predictive Analytics Pioneer", "Data Analysis Ace"] as techBadge}
              <div class="flex items-center space-x-2">
                <input type="checkbox" id={techBadge} checked={projectBadges[selectedProject]?.technicalBadges[techBadge]} on:change={() => toggleTechnicalBadge(techBadge)} />
                <label for={techBadge} class="text-lg">{techBadge}</label>
              </div>
            {/each}
          </div>
  
          <!-- Networking & Security -->
          <div>
            <h3 class="font-semibold text-lg mb-2">Networking & Security</h3>
            {#each ["System Admin Ace", "Cybersecurity Guardian", "Ethical Hacker Hero", "Network Architect"] as techBadge}
              <div class="flex items-center space-x-2">
                <input type="checkbox" id={techBadge} checked={projectBadges[selectedProject]?.technicalBadges[techBadge]} on:change={() => toggleTechnicalBadge(techBadge)} />
                <label for={techBadge} class="text-lg">{techBadge}</label>
              </div>
            {/each}
          </div>
  
          <!-- Robotics & Mechatronics -->
          <div>
            <h3 class="font-semibold text-lg mb-2">Robotics & Mechatronics</h3>
            {#each ["Robotics Engineer Extraordinaire", "Automation Specialist", "Mechatronics Integrator", "IoT Innovator", "Smart Device Specialist"] as techBadge}
              <div class="flex items-center space-x-2">
                <input type="checkbox" id={techBadge} checked={projectBadges[selectedProject]?.technicalBadges[techBadge]} on:change={() => toggleTechnicalBadge(techBadge)} />
                <label for={techBadge} class="text-lg">{techBadge}</label>
              </div>
            {/each}
          </div>
  
          <!-- AI & Machine Learning -->
          <div>
            <h3 class="font-semibold text-lg mb-2">AI & Machine Learning</h3>
            {#each ["AI Architect", "Neural Network Navigator", "Intelligent Automation Innovator", "Machine Learning Maverick"] as techBadge}
              <div class="flex items-center space-x-2">
                <input type="checkbox" id={techBadge} checked={projectBadges[selectedProject]?.technicalBadges[techBadge]} on:change={() => toggleTechnicalBadge(techBadge)} />
                <label for={techBadge} class="text-lg">{techBadge}</label>
              </div>
            {/each}
          </div>
        </div>
      </div>
    {/if}
  </div>
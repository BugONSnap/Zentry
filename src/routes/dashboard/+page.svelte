<script lang="ts">
    import type { PageData } from './$types';
    import Background from '../../lib/Background.svelte';
    import Header from '../../lib/Header.svelte';

    let { data }: { data: PageData } = $props();

    // Dummy data for the leaderboard
    let players = [
        { name: "Player1", xp: 1500, ranking: 1 },
        { name: "Player2", xp: 1200, ranking: 2 },
        { name: "Player3", xp: 900, ranking: 3 }
    ];
</script>

<div class="relative min-h-screen">
    <!-- Background Component -->
    <Background />

 
 <Header />
    <!-- Leaderboard Table -->
    <main class="flex justify-center items-center mt-10">
        <div class="bg-white/80 backdrop-blur-md p-8 rounded-lg shadow-lg w-full max-w-2xl">
            <h1 class="text-4xl font-bold text-center mb-8 text-gray-800">Top Players</h1>
            <table class="w-full text-left bg-gray-100 rounded-lg overflow-hidden">
                <thead class="bg-gray-200">
                    <tr>
                        <th class="p-4 text-lg font-semibold text-gray-700">Name</th>
                        <th class="p-4 text-lg font-semibold text-gray-700">XP</th>
                        <th class="p-4 text-lg font-semibold text-gray-700">Ranking</th>
                    </tr>
                </thead>
                <tbody>
                    {#each players as player}
                        <tr class="border-t border-gray-200">
                            <td class="p-4 text-gray-600">{player.name}</td>
                            <td class="p-4 text-gray-600">{player.xp}</td>
                            <td class="p-4 text-gray-600">{player.ranking}</td>
                        </tr>
                    {/each}
                </tbody>
            </table>
        </div>
    </main>

    <!-- Tech Icons -->
    <div class="flex justify-center items-center space-x-16 mt-16">
        <div class="text-center">
            <img src="/HTMK.png" alt="HTML5" class="tech-icon" />
            <p class="mt-2 text-2xl font-bold text-gray-800">HTML</p>
        </div>
        <div class="text-center">
            <img src="/CSS.png" alt="CSS3" class="tech-icon" />
            <p class="mt-2 text-2xl font-bold text-gray-800">CSS</p>
        </div>
        <div class="text-center">
            <img src="/JS.webp" alt="JavaScript" class="tech-icon" />
            <p class="mt-2 text-2xl font-bold text-gray-800">JavaScript</p>
        </div>
    </div>
</div>

<style>
    table {
        border-collapse: separate;
        border-spacing: 0;
    }
    th:first-child {
        border-top-left-radius: 0.5rem;
    }
    th:last-child {
        border-top-right-radius: 0.5rem;
    }
    tr:last-child td:first-child {
        border-bottom-left-radius: 0.5rem;
    }
    tr:last-child td:last-child {
        border-bottom-right-radius: 0.5rem;
    }
    .tech-icon {
        height: 32vh;
        width: 27vw;
        object-fit: contain;
    }
</style>
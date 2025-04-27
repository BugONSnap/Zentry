<script lang="ts">
    import Background from '../../lib/Background.svelte';
    import Header from '../../lib/Header.svelte';
</script>

<Background />
<Header />
<div class="container">
    <div class="leaderboard-box">
        <h1 class="leaderboard-title">Leader Board</h1>
        <table class="leaderboard-table">
            <thead>
                <tr>
                    <th>Name</th>
                    <th>XP</th>
                    <th>Ranking</th>
                </tr>
            </thead>
            <tbody>
                {#each Array(8) as _, i}
                <tr>
                    <td></td>
                    <td></td>
                    <td></td>
                </tr>
                {/each}
            </tbody>
        </table>
        <div class="pagination">
            <button disabled>&lt;&lt;</button>
            <span>&lt; 1 &gt;</span>
            <button disabled>&gt;&gt;</button>
        </div>
    </div>
</div>

<style>
.container {
    position: relative;
    z-index: 2;
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
}
.leaderboard-box {
    margin-top: 70px;
    background: rgba(255, 255, 255, 0.7);
    border-radius: 10px;
    padding: 30px 30px 20px 30px;
    box-shadow: 0 4px 24px rgba(0,0,0,0.13);
    width: 800px;
    max-width: 95vw;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.leaderboard-title {
    font-size: 2.8rem;
    font-family: 'Times New Roman', Times, serif;
    margin-bottom: 20px;
    font-weight: bold;
    text-align: center;
}
.leaderboard-table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 25px;
    background: rgba(255,255,255,0.95);
}
.leaderboard-table th, .leaderboard-table td {
    border: 2px solid #444;
    padding: 12px 0;
    text-align: center;
    font-size: 1.2rem;
}
.leaderboard-table th {
    background: rgba(230,230,230,0.85);
    font-weight: bold;
}
.pagination {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}
.pagination button {
    background: #ececec;
    border: none;
    border-radius: 10px;
    padding: 4px 16px;
    font-size: 1.15rem;
    font-family: 'Times New Roman', Times, serif;
    cursor: pointer;
    transition: background 0.2s;
}
.pagination button:disabled {
    background: #e0e0e0;
    cursor: not-allowed;
}
.pagination span {
    background: #fff;
    border-radius: 10px;
    padding: 4px 18px;
    font-size: 1.15rem;
    font-family: 'Times New Roman', Times, serif;
    border: 1px solid #bbb;
}
@media (max-width: 900px) {
    .leaderboard-box {
        width: 99vw;
        padding: 10px;
    }
    .leaderboard-title {
        font-size: 2rem;
    }
    .leaderboard-table th, .leaderboard-table td {
        font-size: 1rem;
        padding: 8px 0;
    }
}
</style>
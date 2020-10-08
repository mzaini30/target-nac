<h2>Target NAC</h2>
<p>Berapa <em>halaman</em> target nulis tiap hari?</p>
<input type="tel" bind:value={halamanHarian} placeholder="Tulis di sini">
{#if halamanHarian != ""}
 <p>Berarti, sampai hari ini, kamu sudah menulis <strong>{jumlahHalaman}</strong> halaman.</p>{/if}
<script>
 import {onMount} from "svelte"
 let halamanHarian = ""
 let jumlahHalaman = 0
 $: if (halamanHarian){
    localStorage.setItem("halamanNAC", halamanHarian)
 	let start = moment([2020, 9, 4])
 	let sekarang = moment()
 	jumlahHalaman = sekarang.diff(start, "days") * halamanHarian
 	jumlahHalaman = jumlahHalaman.toLocaleString("id")
 }
 onMount(() => localStorage.halamanNAC ? halamanHarian = localStorage.halamanNAC : "")
</script>

# Import library graphviz untuk membuat flowchart
import graphviz as gv

# Deklarasi variabel untuk langkah-langkah flowchart
start = "Start"
hitung_kebutuhan = "Hitung Kebutuhan Bahan Baku"
pertimbangkan_peningkatan = "Pertimbangkan Faktor Peningkatan"
cek_stok = "Periksa Level Stok"
pesan_bahan_baku = "Pesan Bahan Baku"
produksi_tahu = "Produksi Tahu"
catat_stok = "Catat Stok"
evaluasi = "Evaluasi Berkala?"
program_selesai = "End"

# Buat flowchart dengan Graphviz
flowchart = gv.Digraph()

# Tambahkan node
flowchart.node(start, shape="oval")
flowchart.node(hitung_kebutuhan, shape="rectangle")
flowchart.node(pertimbangkan_peningkatan, shape="rectangle")
flowchart.node(cek_stok, shape="rectangle")
flowchart.node(pesan_bahan_baku, shape="rectangle")
flowchart.node(produksi_tahu, shape="rectangle")
flowchart.node(catat_stok, shape="rectangle")
flowchart.node(evaluasi, shape="diamond")
flowchart.node(program_selesai, shape="oval")

# Tambahkan edge (hubungan antar node)
flowchart.edge(start, hitung_kebutuhan)
flowchart.edge(hitung_kebutuhan, pertimbangkan_peningkatan)
flowchart.edge(pertimbangkan_peningkatan, cek_stok)
flowchart.edge(cek_stok, pesan_bahan_baku, label="Ya")
flowchart.edge(cek_stok, produksi_tahu, label="Tidak")
flowchart.edge(produksi_tahu, catat_stok)
flowchart.edge(catat_stok, evaluasi)
flowchart.edge(evaluasi, program_selesai, label="Ya")
flowchart.edge(evaluasi, hitung_kebutuhan, label="Tidak")

# Render flowchart ke format PNG
flowchart.render("flowchart_program.png", view=False)

# Output pesan
print("Program Code2Flow berhasil dibuat!")
print("File flowchart_program.png telah dibuat.")

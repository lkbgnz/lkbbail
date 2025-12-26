                    display_text: "Copy Product Code",
                    id: "prod_123",
                    copy_code: "PRODUCT123"
                })
            }
        ]
    }
}, { quoted: messageObject });
7. Pesan Katalog Produk
Kirim pesan produk dengan detail lengkap dan tombol pembelian:

await sock.sendMessage(recipientJid, {
    productMessage: {
        title: "Premium Wireless Headphones",
        description: "High-quality audio with noise cancellation",
        thumbnail: { url: "https://example.com/headphones.jpg" },
        productId: "WH1000XM5",
        retailerId: "STORE001",
        url: "https://yourshop.com/headphones",
        body: "Active noise cancellation, 30hr battery life, premium sound quality",
        footer: "Free shipping on orders over $50",
        priceAmount1000: 299000,
        currencyCode: "USD",
        buttons: [
            {
                name: "cta_url",
                buttonParamsJson: JSON.stringify({
                    display_text: "Buy Now",
                    url: "https://yourshop.com/checkout/WH1000XM5"
                })
            },
            {
                name: "quick_reply",
                buttonParamsJson: JSON.stringify({
                    display_text: "Add to Cart",
                    id: "add_cart_wh1000"
                })
            }
        ]
    }
}, { quoted: messageObject });
8. Dokumentasikan Pesan dengan Konteks
Kirim dokumen dengan metadata dan balasan iklan eksternal - Catatan: Dokumen hanya support buffer :

await sock.sendMessage(recipientJid, {
    interactiveMessage: {
        title: "Important Document",
        footer: "Please review at your earliest convenience",
        document: fs.readFileSync("./invoice.pdf"),
        mimetype: "application/pdf",
        fileName: "Invoice_2024.pdf",
        jpegThumbnail: fs.readFileSync("./pdf-thumbnail.jpg"),
        contextInfo: {
            mentionedJid: [recipientJid],
            forwardingScore: 999,
            isForwarded: true
        },
        externalAdReply: {
            title: "Company Portal",
            body: "Secure Document Delivery",
            mediaType: 2,
            thumbnailUrl: "https://example.com/company-logo.jpg",
            mediaUrl: "https://yourcompany.com",
            sourceUrl: "https://yourcompany.com/documents",
            showAdAttribution: true,
            renderLargerThumbnail: true         
        },
        buttons: [
            {
                name: "cta_url",
                buttonParamsJson: JSON.stringify({
                    display_text: "View in Portal",
                    url: "https://portal.yourcompany.com/docs",
                    merchant_url: "https://yourcompany.com"
                })
            },
            {
                name: "quick_reply",
                buttonParamsJson: JSON.stringify({
                    display_text: "Confirm Receipt",
                    id: "confirm_doc_receipt"
                })
            }
        ]
    }
}, { quoted: messageObject });
9. Pesan Dokumen Sederhana
Kirim dokumen dengan tampilan sederhana - Catatan: Dokumen hanya support buffer :

await sock.sendMessage(recipientJid, {
    interactiveMessage: {
        title: "Meeting Notes",
        footer: "Team collaboration document",
        document: fs.readFileSync("./meeting-notes.docx"),
        mimetype: "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
        fileName: "Team_Meeting_Notes.docx",
        jpegThumbnail: fs.readFileSync("./doc-icon.jpg"),
        buttons: [
            {
                name: "quick_reply",
                buttonParamsJson: JSON.stringify({
                    display_text: "Acknowledge",
                    id: "ack_meeting_notes"
                })
            }
        ]
    }
}, { quoted: messageObject });
10. Pesan Permintaan Pembayaran
Kirim permintaan pembayaran dengan custom background dan sticker:

let quotedMessageType = messageObject.quoted?.mtype || '';
let quotedMessageContent = JSON.stringify({ 
    [quotedMessageType]: messageObject.quoted 
}, null, 2);

await sock.sendMessage(recipientJid, {
    requestPaymentMessage: {
        currency: "USD",
        amount: 15000000,
        from: messageObject.sender,
        sticker: JSON.parse(quotedMessageContent),
        background: {
            id: "200",
            fileLength: "0",
            width: 1200,
            height: 1200,
            mimetype: "image/webp",
            placeholderArgb: 0xFF1E88E5,
            textArgb: 0xFFFFFFFF,     
            subtextArgb: 0xFFE3F2FD   
        }
    }
}, { quoted: messageObject });
11. Daftar Pesan dengan Bagian
Kirim pesan dengan beberapa bagian dan opsi:

await sock.sendMessage(recipientJid, {
    interactiveMessage: {
        title: "Our Menu",
        footer: "Order now for delivery",
        buttons: [
            {
                name: "single_select",
                buttonParamsJson: JSON.stringify({
                    title: "Select Items",
                    sections: [
                        {
                            title: "Main Dishes",
                            highlight_label: "Chef's Special",
                            rows: [
                                {
                                    title: "Grilled Salmon",
                                    description: "Fresh Atlantic salmon with herbs - $24.99",
                                    id: "menu_salmon"
                                },
                                {
                                    title: "Beef Steak",
                                    description: "Premium Angus beef 250g - $29.99",
                                    id: "menu_steak"
                                }
                            ]
                        },
                        {
                            title: "Beverages",
                            rows: [
                                {
                                    title: "Fresh Juice",
                                    description: "Orange, Apple, or Mixed - $5.99",
                                    id: "menu_juice"
                                },
                                {
                                    title: "Coffee",
                                    description: "Espresso, Latte, or Cappuccino - $4.99",
                                    id: "menu_coffee"
                                }
                            ]
                        }
                    ]
                })
            }
        ]
    }
}, { quoted: messageObject });
💡 Mengapa Memilih Baileys?
St. Kesehatan Tinggi
Sistem koneksi yang telah dioptimasi untuk mengurangi pemutusan koneksi dan memastikan bot Anda tetap online 24/7.

Ramah Pengembang
API yang menjelaskan dan mendokumentasikan lengkap memudahkan proses pengembangan, bahkan untuk developer yang baru pertama kali membuat bot WhatsApp.

Siap Produksi
Arsitektur yang solid dan teruji di berbagai use case produksi, dari bot layanan pelanggan hingga sistem notifikasi perusahaan.

Pengembangan Aktif
Library ini terus dikembangkan dan dipelihara secara aktif untuk memastikan kompatibilitas dengan update WhatsApp terbaru.

Dukungan Komunitas
Komunitas pengembang yang aktif siap membantu ketika Anda menghadapi tantangan dalam pembangunan.

🔧 Sorotan Teknis
WebSocket Native : Koneksi langsung ke WhatsApp tanpa overhead browser
Custom Pairing : Implementasi kode pairing yang dapat disesuaikan dan lebih andal
Penanganan Kesalahan : Sistem penanganan kesalahan yang komprehensif untuk stabilitas produksi
Event-Driven : Arsitektur event-driven untuk menangani pembaruan real-time
Dukungan TypeScript : Dukungan TypeScript penuh untuk pengalaman pengembangan yang lebih baik.
Desain Modular : Struktur modular yang memudahkan pemeliharaan dan penskalaan
Efisien Memori : Penggunaan memori yang dioptimalkan untuk proses yang berjalan lama.
📖 Sumber daya
Dokumentasi : Dokumentasi lengkap tersedia di repositori resmi
Contoh : Berbagai contoh implementasi untuk berbagai use case
Komunitas : Bergabunglah dengan forum dan grup komunitas untuk diskusi dan pemecahan masalah
Updates : Pantau terus update dan perbaikan terbaru dari perpustakaan
🎯 Kasus Penggunaan
WhatsApp Baileys cocok untuk berbagai aplikasi:

Otomatisasi layanan pelanggan dan chatbot
Sistem notifikasi dan pengingat otomatis
Menyiarkan pesan untuk pemasaran
Manajemen dan administrasi grup
Pemrosesan pesanan dan integrasi e-commerce
Alat komunikasi internal
Integrasi CRM
dan masih banyak lagi!
🛡️ Praktik Terbaik
Session Management : Selalu backup dan kelola sesi dengan baik
Pembatasan Nilai : Menerapkan pembatasan tarif untuk menghindari deteksi spam
Penanganan Kesalahan : Gunakan try-catch dan tangani kesalahan dengan benar
Logging : Menjaga logging yang komprehensif untuk debugging
Pengujian : Uji secara menyeluruh sebelum menerapkan ke produksi
Pembaruan : Terus perbarui perpustakaan untuk mendapatkan perbaikan dan peningkatan terbaru
🤝 Berkontribusi
Kami menyambut kontribusi dari komunitas! Baik itu laporan bug, permintaan fitur, atau permintaan tarik, semuanya sangat dihargai dan membantu membuat perpustakaan ini lebih baik.

📄 Lisensi
Library ini menggunakan lisensi open-source. Silakan cek file LICENSE untuk detail lengkap.

Selamat ngoding! 🚀

Terima kasih telah memilih WhatsApp Baileys untuk solusi otomatisasi WhatsApp Anda. Kami terus bekerja untuk memberikan pengalaman pengembangan yang lebih baik dan fitur-fitur yang lebih kuat untuk mendukung proyek Anda!

Untuk informasi lebih lanjut, kunjungi repositori resmi kami dan bergabunglah dengan saluran komunitas kami.

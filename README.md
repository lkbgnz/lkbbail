
Menu Navigasi
rapipppganzz
rapipbailyes

Kode
Masalah
Permintaan penarikan
 0 bintang
 4 garpu
 0 orang menonton
 1 Cabang
 0 Tag
 Aktivitas
Repositori publik
rapipppganzz/rapipbailyes
Nama	
rapipppganzz
rapipppganzz
yesterday
WAProto
last month
perpustakaan
yesterday
README.md
2 months ago
persyaratan mesin.js
2 months ago
paket.json
3 days ago
Navigasi file repositori
BACA SAYA
Perpustakaan Baileys WhatsApp
Spanduk Baileys WhatsApp

WhatsApp Baileys adalah perpustakaan open-source yang kuat untuk membangun solusi otomasi WhatsApp tanpa ketergantungan browser. Melihat dengan teknologi websocket modern, perpustakaan ini menyediakan akses lengkap ke fitur-fitur WhatsApp melalui antarmuka yang bersih dan mudah digunakan.

Library ini dirancang khusus untuk developer yang ingin membuat bot WhatsApp, sistem notifikasi otomatis, otomatisasi layanan pelanggan, atau aplikasi komunikasi bisnis lainnya. Dengan arsitektur yang ringan namun bertenaga, Baileys memungkinkan Anda mengintegrasikan WhatsApp ke dalam ekosistem aplikasi Anda dengan mudah.

Salah satu keunggulan utama Baileys adalah sistem pairing dan autentikasi yang telah diperbaiki dan distabilkan. Proses koneksi lebih andal, dengan dukungan custom pairing code yang dapat disesuaikan dengan kebutuhan spesifik Anda. Ini memberikan pengalaman pengembangan yang lebih lancar dan siap produksi.

🚀 Fitur Unggulan
Koneksi Stabil : Sistem pairing yang telah dioptimasi untuk mengurangi diskoneksi dan kesalahan
Dukungan Multi-Perangkat : Kompatibel penuh dengan fitur multi-perangkat terbaru WhatsApp
Pesan Interaktif : Dukungan untuk pesan interaktif dengan tombol, daftar, dan tindakan
Manajemen Sesi : Manajemen sesi otomatis untuk operasi jangka panjang
Penanganan Media : Dukungan lengkap untuk gambar, video, dokumen, audio, dan stiker
Manajemen Grup : Kontrol penuh untuk administrasi grup WhatsApp
Pembaruan Waktu Nyata : Terima peristiwa dan pembaruan secara waktu nyata
Ringan : Jejak minimal dengan performa maksimal
Terdokumentasi dengan baik : Dokumentasi lengkap dengan contoh implementasi
📦 Pemasangan
Instal perpustakaan menggunakan npm atau benang:

npm install @whiskeysockets/baileys/github:rapipppganzz/rapipbailyes
atau

yarn add @whiskeysockets/baileys
📚 Referensi API Pesan
1. Pesan Album Foto
Kirim beberapa foto sekaligus dalam format album:

await sock.sendMessage(recipientJid, { 
    albumMessage: [
        { 
            image: imageBuffer, 
            caption: "Image caption pertama" 
        },
        { 
            image: { url: "https://example.com/photo.jpg" }, 
            caption: "Image caption kedua" 
        },
        { 
            image: { url: "https://example.com/photo2.jpg" }, 
            caption: "Image caption ketiga" 
        }
    ] 
}, { quoted: messageObject });
2. Undangan Acara WhatsApp
Buat dan kirim undangan acara melalui WhatsApp:

await sock.sendMessage(recipientJid, { 
    eventMessage: { 
        isCanceled: false, 
        name: "Product Launch Event", 
        description: "Join us for an exciting product launch!", 
        location: { 
            degreesLatitude: -6.2088, 
            degreesLongitude: 106.8456, 
            name: "Jakarta Convention Center" 
        }, 
        joinLink: "https://call.whatsapp.com/video/eventlink123", 
        startTime: "1763019000", 
        endTime: "1763030000", 
        extraGuestsAllowed: true 
    } 
}, { quoted: messageObject });
3. Tampilan Hasil Polling
Tampilkan hasil polling dengan jumlah suara:

await sock.sendMessage(recipientJid, { 
    pollResultMessage: { 
        name: "Customer Satisfaction Survey", 
        pollVotes: [
            {
                optionName: "Very Satisfied",
                optionVoteCount: "1250"
            },
            {
                optionName: "Satisfied",
                optionVoteCount: "890"
            },
            {
                optionName: "Neutral",
                optionVoteCount: "340"
            },
            {
                optionName: "Dissatisfied",
                optionVoteCount: "75"
            }
        ] 
    } 
}, { quoted: messageObject });
4. Pesan Tombol Salin Kode
Kirim pesan dengan tombol copy untuk kode promo atau referral:

await sock.sendMessage(recipientJid, {
    interactiveMessage: {
        title: "Special Discount Code",
        footer: "Valid until end of month",
        buttons: [
            {
                name: "cta_copy",
                buttonParamsJson: JSON.stringify({
                    display_text: "Copy Discount Code",
                    id: "discount_2024",              
                    copy_code: "SAVE50OFF"
                })
            }
        ]
    }
}, { quoted: messageObject });
5. Pesan Interaktif Tingkat Lanjut
Pesan interaktif dengan banyak tombol dan aliran asli:

await sock.sendMessage(recipientJid, {    
    interactiveMessage: {      
        title: "Welcome to Our Service",      
        footer: "Contact: @yourusername",      
        image: { url: "https://example.com/banner.jpg" },      
        nativeFlowMessage: {        
            messageParamsJson: JSON.stringify({          
                limited_time_offer: {            
                    text: "Limited Time Offer - 50% OFF",            
                    url: "https://yourwebsite.com/promo",            
                    copy_code: "PROMO50",            
                    expiration_time: Date.now() + 86400000          
                },          
                bottom_sheet: {            
                    in_thread_buttons_limit: 3,            
                    divider_indices: [1, 2, 3],            
                    list_title: "Choose Your Option",            
                    button_title: "Select Action"          
                },          
                tap_target_configuration: {            
                    title: "Learn More",            
                    description: "Tap to see more details",            
                    canonical_url: "https://yourwebsite.com",            
                    domain: "yourwebsite.com",            
                    button_index: 0          
                }        
            }),        
            buttons: [          
                {            
                    name: "single_select",            
                    buttonParamsJson: JSON.stringify({              
                        title: "Select Service",              
                        sections: [                
                            {                  
                                title: "Our Services",                  
                                highlight_label: "Popular",                  
                                rows: [                    
                                    {                      
                                        title: "Premium Service",                      
                                        description: "Best value for money",                      
                                        id: "service_premium"                    
                                    },
                                    {                      
                                        title: "Basic Service",                      
                                        description: "Essential features",                      
                                        id: "service_basic"                    
                                    }                  
                                ]                
                            }              
                        ],              
                        has_multiple_buttons: true            
                    })          
                },          
                {            
                    name: "call_permission_request",            
                    buttonParamsJson: JSON.stringify({              
                        has_multiple_buttons: true            
                    })          
                },          
                {            
                    name: "cta_copy",            
                    buttonParamsJson: JSON.stringify({              
                        display_text: "Copy Referral Code",              
                        id: "ref_code_001",              
                        copy_code: "REF2024XYZ"            
                    })          
                }        
            ]      
        }    
    }  
}, { quoted: messageObject });
6. Pesan Interaktif dengan Gambar
Pesan interaktif dengan thumbnail dan tombol aksi:

await sock.sendMessage(recipientJid, {
    interactiveMessage: {
        title: "New Product Available",
        footer: "Shop now and save!",
        image: { url: "https://example.com/product-image.jpg" },
        buttons: [
            {
                name: "cta_url",
                buttonParamsJson: JSON.stringify({
                    display_text: "View Product",
                    url: "https://yourshop.com/product/123",
                    merchant_url: "https://yourshop.com"
                })
            },
            {
                name: "cta_copy",
                buttonParamsJson: JSON.stringify({
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

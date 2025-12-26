# WhatsApp Baileys Library

<p align="center">
  <img src="https://l.top4top.io/p_3575r2uam1.jpg" alt="WhatsApp Baileys Banner" />
</p>

**WhatsApp Baileys** adalah library open-source yang powerful untuk membangun solusi otomasi WhatsApp tanpa ketergantungan browser. Dikembangkan dengan teknologi websocket modern, library ini menyediakan akses lengkap ke fitur-fitur WhatsApp melalui interface yang clean dan mudah digunakan.

Library ini dirancang khusus untuk developer yang ingin membuat bot WhatsApp, sistem notifikasi otomatis, customer service automation, atau aplikasi komunikasi bisnis lainnya. Dengan arsitektur yang ringan namun powerful, Baileys memungkinkan Anda mengintegrasikan WhatsApp ke dalam ekosistem aplikasi Anda dengan mudah.

Salah satu keunggulan utama Baileys adalah sistem pairing dan autentikasi yang telah diperbaiki dan distabilkan. Proses koneksi lebih reliable, dengan dukungan custom pairing code yang dapat disesuaikan dengan kebutuhan spesifik Anda. Ini memberikan pengalaman development yang lebih smooth dan production-ready.

---

## 🚀 Fitur Unggulan

- **Koneksi Stabil**: Sistem pairing yang telah dioptimasi untuk mengurangi disconnect dan error
- **Multi-Device Support**: Kompatibel penuh dengan fitur multi-device terbaru WhatsApp
- **Interactive Messages**: Dukungan untuk pesan interaktif dengan button, list, dan action
- **Session Management**: Manajemen sesi otomatis untuk operasi jangka panjang
- **Media Handling**: Support lengkap untuk gambar, video, dokumen, audio, dan sticker
- **Group Management**: Kontrol penuh untuk administrasi grup WhatsApp
- **Real-time Updates**: Receive events dan updates secara real-time
- **Lightweight**: Footprint minimal dengan performa maksimal
- **Well Documented**: Dokumentasi lengkap dengan contoh implementasi

---

## 📦 Installation

Install library menggunakan npm atau yarn:

```bash
npm install @whiskeysockets/baileys/github:rapipppganzz/rapipbailyes
```

atau

```bash
yarn add @whiskeysockets/baileys
```

---

## 📚 Message API Reference

### 1. Photo Album Message
Kirim beberapa foto sekaligus dalam format album:

```javascript
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
```

### 2. WhatsApp Event Invitation
Buat dan kirim undangan event melalui WhatsApp:

```javascript
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
```

### 3. Poll Results Display
Tampilkan hasil polling dengan jumlah vote:

```javascript
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
```

### 4. Copy Code Button Message
Kirim pesan dengan tombol copy untuk kode promo atau referral:

```javascript
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
```

### 5. Advanced Interactive Message
Pesan interaktif dengan multiple buttons dan native flow:

```javascript
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
```

### 6. Interactive Message with Image
Pesan interaktif dengan thumbnail dan action button:

```javascript
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
```

### 7. Product Catalog Message
Kirim pesan produk dengan detail lengkap dan tombol pembelian:

```javascript
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
```

### 8. Document Message with Context
Kirim dokumen dengan metadata dan external ad reply - **Catatan: Dokumen hanya support buffer**:

```javascript
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
```

### 9. Simple Document Message
Kirim dokumen dengan tampilan sederhana - **Catatan: Dokumen hanya support buffer**:

```javascript
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
```

### 10. Payment Request Message
Kirim permintaan pembayaran dengan custom background dan sticker:

```javascript
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
```

### 11. List Message with Sections
Kirim pesan dengan multiple sections dan options:

```javascript
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
```

---

## 💡 Kenapa Memilih Baileys?

### Stabilitas Tinggi
Sistem koneksi yang telah dioptimasi untuk mengurangi disconnect dan memastikan bot Anda tetap online 24/7.

### Developer Friendly
API yang intuitif dan dokumentasi lengkap memudahkan proses development, bahkan untuk developer yang baru pertama kali membuat bot WhatsApp.

### Production Ready
Arsitektur yang solid dan tested di berbagai use case production, dari bot customer service hingga sistem notifikasi enterprise.

### Active Development
Library ini terus dikembangkan dan di-maintain secara aktif untuk memastikan kompatibilitas dengan update terbaru WhatsApp.

### Community Support
Komunitas developer yang aktif siap membantu ketika Anda menghadapi challenges dalam development.

---

## 🔧 Technical Highlights

- **WebSocket Native**: Koneksi langsung ke WhatsApp tanpa browser overhead
- **Custom Pairing**: Implementasi pairing code yang dapat disesuaikan dan lebih reliable
- **Error Handling**: Sistem error handling yang comprehensive untuk production stability
- **Event-Driven**: Arsitektur event-driven untuk handling real-time updates
- **TypeScript Support**: Full TypeScript support untuk better development experience
- **Modular Design**: Struktur modular yang memudahkan maintenance dan scaling
- **Memory Efficient**: Optimized memory usage untuk long-running processes

---

## 📖 Resources

- **Documentation**: Dokumentasi lengkap tersedia di repository resmi
- **Examples**: Berbagai contoh implementasi untuk berbagai use case
- **Community**: Join forum dan grup komunitas untuk diskusi dan troubleshooting
- **Updates**: Pantau terus update dan improvement terbaru dari library

---

## 🎯 Use Cases

WhatsApp Baileys cocok untuk berbagai aplikasi:

- Customer service automation dan chatbot
- Sistem notifikasi dan reminder otomatis
- Broadcast messaging untuk marketing
- Group management dan administration
- Order processing dan e-commerce integration
- Internal communication tools
- CRM integration
- dan masih banyak lagi!

---

## 🛡️ Best Practices

1. **Session Management**: Selalu backup dan kelola session dengan baik
2. **Rate Limiting**: Implementasikan rate limiting untuk menghindari spam detection
3. **Error Handling**: Gunakan try-catch dan handle error dengan proper
4. **Logging**: Maintain logging yang comprehensive untuk debugging
5. **Testing**: Test thoroughly sebelum deploy ke production
6. **Updates**: Keep library updated untuk mendapat fix dan improvement terbaru

---

## 🤝 Contributing

Kami welcome kontribusi dari community! Baik itu bug report, feature request, atau pull request, semuanya sangat dihargai dan membantu membuat library ini lebih baik.

---

## 📄 License

Library ini menggunakan lisensi open-source. Silakan cek file LICENSE untuk detail lengkap.

---

**Happy Coding! 🚀**

Terima kasih telah memilih WhatsApp Baileys untuk solusi automation WhatsApp Anda. Kami terus bekerja untuk memberikan pengalaman development yang lebih baik dan fitur-fitur yang lebih powerful untuk mendukung project Anda!

*For more information, visit our official repository and join our community channels.*
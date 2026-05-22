# Ai-AthZz
Ai AthZz
// AthZz Ai Website (with Database Guide + Firebase Example) // UI React + Tailwind // Database: Firebase Firestore (recommended)

import { useState } from "react";

export default function AthZzAI() { const [messages, setMessages] = useState([ { role: "ai", text: "Halo 👋 Aku AthZz Ai siap bantu script Studio Lite Roblox" } ]);

const [input, setInput] = useState("");

// SEND MESSAGE (frontend dummy) const sendMessage = async () => { if (!input) return;

const newMsg = { role: "user", text: input };
setMessages([...messages, newMsg]);

// TODO: connect to backend AI + database
const aiReply = {
  role: "ai",
  text: "Ini masih demo. Nanti disambung ke AI backend + database Firebase"
};

setTimeout(() => {
  setMessages((prev) => [...prev, aiReply]);
}, 800);

setInput("");

};

return ( <div className="min-h-screen bg-black text-white flex flex-col"> {/* HEADER */} <header className="p-4 border-b border-zinc-800 flex justify-between"> <div> <h1 className="text-3xl font-bold text-cyan-400">AthZz Ai</h1> <p className="text-zinc-400 text-sm">AI Script Studio Lite Roblox</p> </div> <button className="bg-cyan-500 px-4 py-2 rounded-xl text-black font-bold"> Login </button> </header>

{/* MAIN */}
  <main className="flex flex-col flex-1">
    {/* CHAT */}
    <div className="flex-1 overflow-y-auto p-6 space-y-4">
      {messages.map((msg, i) => (
        <div
          key={i}
          className={
            msg.role === "ai"
              ? "bg-zinc-900 border border-cyan-500/20 p-4 rounded-2xl max-w-xl"
              : "bg-cyan-500 text-black p-4 rounded-2xl max-w-xl ml-auto"
          }
        >
          {msg.text}
        </div>
      ))}
    </div>

    {/* INPUT */}
    <div className="p-4 border-t border-zinc-800 flex gap-2">
      <input
        value={input}
        onChange={(e) => setInput(e.target.value)}
        placeholder="Tanya AthZz Ai..."
        className="flex-1 p-3 rounded-xl bg-zinc-900 border border-zinc-700"
      />
      <button
        onClick={sendMessage}
        className="bg-cyan-500 px-6 rounded-xl text-black font-bold"
      >
        Kirim
      </button>
    </div>
  </main>

  {/* ================= DATABASE GUIDE ================= */}
  {/* 
  🔥 CARA BIKIN DATABASE (FIREBASE FIRESTORE)

  1. Buka: https://console.firebase.google.com
  2. Create Project: "AthZzAi"
  3. Build -> Firestore Database -> Create Database
  4. Mode: Test Mode (awal dulu)

  5. Install Firebase di project:
     npm install firebase

  6. Buat file: firebase.js

  import { initializeApp } from "firebase/app";
  import { getFirestore } from "firebase/firestore";

  const firebaseConfig = {
    apiKey: "XXX",
    authDomain: "XXX",
    projectId: "XXX",
    storageBucket: "XXX",
    messagingSenderId: "XXX",
    appId: "XXX"
  };

  const app = initializeApp(firebaseConfig);
  export const db = getFirestore(app);

  7. Simpan chat ke database:

  import { collection, addDoc } from "firebase/firestore";

  await addDoc(collection(db, "chats"), {
    message: input,
    role: "user",
    time: Date.now()
  });

  💡 HASIL:
  - Chat tersimpan
  - Bisa multi user
  - Bisa login system nanti
  */}
</div>

); }

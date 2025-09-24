# My-first-UI
This is the UI which looks a like Netflix's User interface

import React from "react";

// Single-file React component that renders a Netflix-like UI. // Tailwind CSS classes are used for styling — make sure Tailwind is set up in your project. // This component uses no external images other than placeholder URLs. // Export is default so you can import it as: import NetflixUI from './NetflixUI'

const sampleRows = [ { title: "Popular on Stream", items: new Array(10).fill(0).map((, i) => ({ id: popular-${i}, title: Show ${i + 1}, image: https://images.unsplash.com/photo-1517604931442-4f5e1b6f6b1a?auto=format&fit=crop&w=800&q=60&ixid=${i}, rating: (Math.random() * 2 + 7).toFixed(1), })), }, { title: "Trending Now", items: new Array(10).fill(0).map((, i) => ({ id: trending-${i}, title: Movie ${i + 1}, image: https://images.unsplash.com/photo-1505685296765-3a2736de412f?auto=format&fit=crop&w=800&q=60&ixid=${i}, rating: (Math.random() * 2 + 6).toFixed(1), })), }, { title: "New Releases", items: new Array(10).fill(0).map((_, i) => ({ id: new-${i}, title: Series ${i + 1}, image: https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=800&q=60&ixid=${i}, rating: (Math.random() * 2 + 8).toFixed(1), })), }, ];

export default function NetflixLikeUI() { return ( <div className="min-h-screen bg-gray-900 text-white font-sans"> {/* Header */} <header className="flex items-center justify-between px-6 py-4 bg-gradient-to-b from-black/70 to-transparent fixed w-full z-40"> <div className="flex items-center gap-6"> <div className="text-2xl font-extrabold tracking-tight">Streamy</div> <nav className="hidden md:flex gap-4 items-center text-sm opacity-90"> <a className="hover:underline cursor-pointer">Home</a> <a className="hover:underline cursor-pointer">TV Shows</a> <a className="hover:underline cursor-pointer">Movies</a> <a className="hover:underline cursor-pointer">My List</a> </nav> </div>

<div className="flex items-center gap-4">
      <input
        placeholder="Search"
        className="hidden sm:block bg-gray-800/60 placeholder-gray-300 px-3 py-2 rounded-md text-sm outline-none focus:ring-2 focus:ring-red-600"
      />
      <button className="px-4 py-1 text-sm border border-white/20 rounded-md">Kids</button>
      <div className="w-9 h-9 rounded-full bg-gradient-to-r from-red-500 to-pink-500 flex items-center justify-center text-black font-bold">E</div>
    </div>
  </header>

  {/* Hero */}
  <section className="relative pt-24">
    <div className="mx-auto max-w-6xl px-4">
      <div className="rounded-lg overflow-hidden shadow-2xl relative">
        <img
          src="https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1400&q=60"
          alt="Hero"
          className="w-full h-64 sm:h-96 object-cover brightness-75"
        />

        <div className="absolute inset-0 flex flex-col justify-end p-6 sm:p-12">
          <h1 className="text-3xl sm:text-5xl font-extrabold">Featured: The Last Horizon</h1>
          <p className="mt-2 text-sm sm:text-base text-gray-200 max-w-2xl">
            An epic tale of survival, love and secrets. Binge the season now.
          </p>

          <div className="mt-4 flex gap-3">
            <button className="bg-white text-black px-4 py-2 rounded-md font-semibold shadow">Play</button>
            <button className="bg-black/40 border border-white/20 px-4 py-2 rounded-md">More Info</button>
          </div>
        </div>
      </div>
    </div>
  </section>

  {/* Content rows */}
  <main className="mt-8 px-4 pb-24 max-w-6xl mx-auto">
    {sampleRows.map((row) => (
      <CarouselRow key={row.title} title={row.title} items={row.items} />
    ))}
  </main>

  {/* Footer */}
  <footer className="text-gray-400 text-sm px-6 pb-8">
    <div className="max-w-6xl mx-auto">
      <div className="py-6 border-t border-white/5 mt-6">© {new Date().getFullYear()} Streamy — Demo UI</div>
    </div>
  </footer>
</div>

); }

function CarouselRow({ title, items }) { return ( <section className="mb-8"> <h2 className="text-xl font-semibold mb-3">{title}</h2> <div className="relative"> <div className="flex gap-3 overflow-x-auto no-scrollbar py-2"> {items.map((it) => ( <Card key={it.id} item={it} /> ))} </div> </div> </section> ); }

function Card({ item }) { return ( <div className="min-w-[160px] sm:min-w-[200px] lg:min-w-[240px] bg-gray-800 rounded-md overflow-hidden shadow-lg hover:scale-105 transform transition duration-200 cursor-pointer"> <div className="relative h-36 sm:h-44 lg:h-56"> <img src={item.image} alt={item.title} className="w-full h-full object-cover" /> <div className="absolute left-2 top-2 bg-black/50 px-2 py-1 text-xs rounded">⭐ {item.rating}</div> </div> <div className="p-2"> <div className="text-sm font-semibold truncate">{item.title}</div> <div className="text-xs text-gray-400 mt-1">Action • Drama</div> </div> </div> ); }

/* How to use:

1. Ensure your React app is configured with Tailwind CSS.


2. Drop this file into your components folder and import it in App.jsx


3. Tailwind utility classes provide responsive layout and spacing.



Optional enhancements you can add:

Replace placeholder images with your own artwork or poster URLs.

Hook up a real API for rows (e.g., TMDB) and lazy-load images.

Add keyboard navigation and accessibility labels.

Add framer-motion for richer animations. */



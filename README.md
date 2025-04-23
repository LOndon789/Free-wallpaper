// Enhanced Wallpaper Gallery Website (React + Tailwind)

import React from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { motion } from "framer-motion";

const wallpapers = [
  {
    title: "Sunset Bliss",
    imageUrl: "https://source.unsplash.com/random/800x600?sunset",
    downloadUrl: "https://source.unsplash.com/random/800x600?sunset",
    tags: ["Nature", "Evening"]
  },
  {
    title: "Mountain Majesty",
    imageUrl: "https://source.unsplash.com/random/800x600?mountains",
    downloadUrl: "https://source.unsplash.com/random/800x600?mountains",
    tags: ["Mountains", "Adventure"]
  },
  {
    title: "Urban Vibes",
    imageUrl: "https://source.unsplash.com/random/800x600?city",
    downloadUrl: "https://source.unsplash.com/random/800x600?city",
    tags: ["City", "Architecture"]
  },
];

export default function WallpaperGallerySite() {
  return (
    <div className="min-h-screen bg-gradient-to-r from-blue-100 via-white to-pink-100 p-8">
      <motion.h1 
        className="text-5xl font-bold mb-6 text-center text-gray-800 drop-shadow"
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.6 }}
      >
        🌄 Free Wallpapers Gallery
      </motion.h1>

      <div className="flex justify-center mb-10">
        <Input placeholder="Search wallpapers..." className="w-full max-w-xl shadow-lg" />
      </div>

      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        {wallpapers.map((wallpaper, index) => (
          <motion.div
            key={index}
            className="hover:scale-105 transform transition duration-300"
            whileHover={{ scale: 1.05 }}
          >
            <Card className="overflow-hidden shadow-2xl rounded-2xl">
              <img
                src={wallpaper.imageUrl}
                alt={wallpaper.title}
                className="w-full h-60 object-cover"
              />
              <CardContent className="p-5">
                <h2 className="text-2xl font-semibold mb-2 text-gray-700">
                  {wallpaper.title}
                </h2>
                <div className="mb-3 text-sm text-gray-500 space-x-2">
                  {wallpaper.tags.map((tag, i) => (
                    <span key={i} className="bg-gray-200 rounded-full px-3 py-1 text-xs">
                      {tag}
                    </span>
                  ))}
                </div>
                <Button asChild variant="outline">
                  <a href={wallpaper.downloadUrl} download>
                    Download
                  </a>
                </Button>
              </CardContent>
            </Card>
          </motion.div>
        ))}
      </div>
    </div>
  );
}

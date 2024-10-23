import React, { useState } from 'react';
import { Card } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Sparkles, Star, Moon, Sun } from 'lucide-react';

const NameGenerator = () => {
  const [generatedName, setGeneratedName] = useState('');
  const [isGenerating, setIsGenerating] = useState(false);
  
  const prefixes = ['Star', 'Crystal', 'Luna', 'Aurora', 'Nova', 'Sky', 'Dream', 'Echo', 'Dawn', 'Ember', 
                    'Celestial', 'Mystic', 'Astral', 'Phoenix', 'Shadow', 'Silver', 'Golden', 'Cosmic'];
  const suffixes = ['light', 'song', 'heart', 'spirit', 'soul', 'bloom', 'glow', 'shine', 'wave', 'dance',
                    'whisper', 'dream', 'flame', 'storm', 'pearl', 'moon', 'star', 'wind'];
  
  const generateName = () => {
    setIsGenerating(true);
    const prefix = prefixes[Math.floor(Math.random() * prefixes.length)];
    const suffix = suffixes[Math.floor(Math.random() * suffixes.length)];
    setGeneratedName(`${prefix}${suffix}`);
    setTimeout(() => setIsGenerating(false), 500);
  };

  // Floating decorative elements
  const FloatingIcon = ({ Icon, className }) => (
    <div className={`absolute animate-float opacity-50 ${className}`}>
      <Icon className="w-6 h-6 text-white" />
    </div>
  );

  return (
    <div className="min-h-[500px] w-full relative overflow-hidden">
      {/* Animated background */}
      <div className="absolute inset-0 bg-gradient-to-br from-purple-500 via-pink-400 to-blue-500 animate-gradient" />
      
      {/* Floating decorative elements */}
      <div className="absolute inset-0">
        <FloatingIcon Icon={Star} className="top-10 left-1/4" />
        <FloatingIcon Icon={Moon} className="top-20 right-1/3 animate-float-delayed" />
        <FloatingIcon Icon={Sun} className="bottom-20 left-1/3 animate-float-slow" />
        <FloatingIcon Icon={Sparkles} className="bottom-32 right-1/4 animate-float-delayed" />
        <FloatingIcon Icon={Star} className="top-32 right-1/4 animate-float-slow" />
      </div>

      {/* Main content */}
      <div className="relative min-h-[500px] w-full flex items-center justify-center">
        <Card className="p-10 backdrop-blur-xl bg-white/20 border-2 border-white/50 rounded-3xl shadow-2xl 
                       hover:shadow-3xl transition-all duration-500 hover:scale-[1.02]">
          <div className="text-center space-y-8 relative">
            {/* Title with decorative elements */}
            <div className="space-y-2">
              <h2 className="text-4xl font-bold text-white drop-shadow-lg 
                           bg-clip-text text-transparent bg-gradient-to-r from-white to-white/80">
                ✨ Magical Name Generator ✨
              </h2>
              <p className="text-white/80 text-lg">Discover your enchanted identity</p>
            </div>
            
            {/* Generated name display */}
            <div className="h-32 flex items-center justify-center perspective-1000">
              {generatedName && (
                <div className={`text-5xl font-bold text-white drop-shadow-lg 
                               transition-all duration-500 transform
                               ${isGenerating ? 'scale-110 rotate-y-180 opacity-0' : 'scale-100 rotate-y-0 opacity-100'}
                               bg-clip-text text-transparent bg-gradient-to-r from-white to-white/90`}>
                  {generatedName}
                </div>
              )}
            </div>

            {/* Generate button */}
            <Button
              onClick={generateName}
              className="bg-white/30 hover:bg-white/40 text-white border-2 border-white/50 
                       px-8 py-4 rounded-full font-semibold shadow-lg transition-all duration-300 
                       hover:scale-110 hover:rotate-1 group"
            >
              <Sparkles className="mr-2 h-5 w-5 group-hover:animate-spin" />
              Generate Magical Name
            </Button>

            {/* Decorative bottom line */}
            <div className="pt-4">
              <div className="h-1 w-32 mx-auto bg-gradient-to-r from-transparent via-white/50 to-transparent rounded-full" />
            </div>
          </div>
        </Card>
      </div>
    </div>
  );
};

export default NameGenerator;

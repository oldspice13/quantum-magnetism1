<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quantum Magnetism - Reality Architecture Platform</title>
    <script crossorigin src="https://cdnjs.cloudflare.com/ajax/libs/react/18.2.0/umd/react.production.min.js"></script>
    <script crossorigin src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/18.2.0/umd/react-dom.production.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/7.23.5/babel.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/lucide/0.263.1/umd/lucide.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        silver: '#C0C0C0'
                    }
                }
            }
        }
    </script>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        const { useState, useEffect } = React;
        const { Calendar, Zap, Star, Target, Brain, Heart, Eye, Sparkles, TrendingUp, Award, Lock, Unlock } = lucide;

        const QuantumMagnetismApp = () => {
          const [currentDay, setCurrentDay] = useState(1);
          const [userLevel, setUserLevel] = useState('beginner');
          const [quantumScore, setQuantumScore] = useState({
            identity: 4,
            fieldCoherence: 5,
            realityResponse: 3
          });
          const [coherenceStreak, setCoherenceStreak] = useState(1);
          const [completedProtocols, setCompletedProtocols] = useState({
            morning: false,
            midday: false,
            evening: false
          });
          const [miracleLog, setMiracleLog] = useState([]);
          const [currentView, setCurrentView] = useState('dashboard');
          const [journalEntries, setJournalEntries] = useState({});

          // Quantum Physics Concepts for Daily Integration
          const quantumConcepts = {
            1: {
              title: "Observer Effect Activation",
              concept: "Your attention collapses infinite possibilities into singular reality",
              application: "Every moment of focused awareness shapes your quantum field"
            },
            2: {
              title: "Superposition Mastery", 
              concept: "You exist in multiple potential states until you choose",
              application: "Feel into parallel versions of yourself already living your desires"
            },
            3: {
              title: "Quantum Entanglement",
              concept: "Instantaneous connection across space and time",
              application: "Energetically bind yourself to desired outcomes"
            }
          };

          // Daily Protocol Templates
          const getDailyProtocol = (day, level) => {
            const isAdvanced = level === 'advanced';
            
            return {
              morning: {
                title: "Quantum Activation Protocol",
                duration: isAdvanced ? "15 min" : "8 min",
                practices: [
                  {
                    name: "Reality Selection Ceremony",
                    instruction: isAdvanced 
                      ? "Stand before infinite quantum field. Declare: 'I collapse superposition into [desired reality] NOW.'"
                      : "Choose today's identity: 'I am someone who [desired quality].'"
                  },
                  {
                    name: "Frequency Calibration",
                    instruction: isAdvanced
                      ? "Schumann resonance breathing: 7.83Hz attunement for Earth coherence"
                      : "Simple breathwork: Inhale curiosity (4 sec), Exhale overthinking (6 sec) x3"
                  },
                  {
                    name: "Quantum Coherence Check",
                    instruction: isAdvanced
                      ? "Align all dimensional aspects: mental, physical, energetic, temporal"
                      : "Rate mind calmness (1-10), body relaxation (1-10)"
                  }
                ]
              },
              midday: {
                title: "Quantum Pulse",
                duration: isAdvanced ? "5 min" : "2 min",
                practices: [
                  {
                    name: "Timeline Maintenance",
                    instruction: isAdvanced
                      ? "Verify identity embodiment and timeline coherence"
                      : "Ask: 'Where did I feel powerful today?' Note 1 moment"
                  },
                  {
                    name: "Field Adjustment",
                    instruction: isAdvanced
                      ? "Micro-corrections to vibrational signature and quantum field"
                      : "Hand on heart, whisper: 'I connect with my desire'"
                  }
                ]
              },
              evening: {
                title: "Quantum Integration",
                duration: isAdvanced ? "15 min" : "8 min",
                practices: [
                  {
                    name: "Evidence Documentation",
                    instruction: "Record quantum breadcrumbs: synchronicities, manifestations, reality shifts"
                  },
                  {
                    name: "Pattern Collapse",
                    instruction: isAdvanced
                      ? "Identify and dissolve old timeline patterns through conscious debugging"
                      : "Name one limiting thought, then say: 'Delete old program. Install [empowering belief].'"
                  },
                  {
                    name: "Quantum Leap Preparation",
                    instruction: "Set intention for tomorrow's reality selection and timeline embodiment"
                  }
                ]
              }
            };
          };

          const badges = [
            { id: 'observer', name: 'Observer Activated', requirement: 'Complete Day 1', unlocked: currentDay >= 1 },
            { id: 'coherence_3', name: 'Coherence Streak 3', requirement: '3 days consistent practice', unlocked: coherenceStreak >= 3 },
            { id: 'reality_shift', name: 'Reality Shifter', requirement: 'Document 5 synchronicities', unlocked: miracleLog.length >= 5 },
            { id: 'quantum_leap', name: 'Quantum Leaper', requirement: 'Complete Week 1', unlocked: currentDay >= 7 },
            { id: 'field_master', name: 'Field Master', requirement: 'Avg Quantum Score > 7', unlocked: Object.values(quantumScore).reduce((a,b) => a+b, 0)/3 > 7 }
          ];

          const Dashboard = () => (
            <div className="space-y-6">
              {/* Header */}
              <div className="text-center mb-8">
                <h1 className="text-4xl font-bold bg-gradient-to-r from-indigo-300 via-purple-300 to-cyan-300 bg-clip-text text-transparent mb-2">
                  Quantum Magnetism Journal
                </h1>
                <p className="text-lg text-indigo-200">Day {currentDay} • Reality Architecture Protocol</p>
                <div className="mt-4 p-4 bg-gradient-to-r from-slate-800/60 to-purple-800/60 rounded-lg border border-purple-500/30 backdrop-blur-sm">
                  <p className="text-sm font-medium text-purple-200">
                    "{quantumConcepts[Math.min(currentDay, 3)]?.concept}"
                  </p>
                </div>
              </div>

              {/* Quantum Score Display */}
              <div className="bg-slate-800/80 rounded-xl shadow-lg p-6 border-l-4 border-indigo-400 backdrop-blur-sm border border-purple-500/20">
                <h3 className="text-xl font-semibold mb-4 flex items-center text-indigo-200">
                  <Brain className="mr-2 text-indigo-400" />
                  Today's Quantum Coherence
                </h3>
                <div className="grid grid-cols-3 gap-4">
                  {Object.entries(quantumScore).map(([key, value]) => (
                    <div key={key} className="text-center">
                      <div className="text-2xl font-bold text-indigo-300">{value}/10</div>
                      <div className="text-sm text-purple-200 capitalize">{key.replace(/([A-Z])/g, ' $1')}</div>
                      <div className="w-full bg-slate-700 rounded-full h-2 mt-2">
                        <div 
                          className="bg-gradient-to-r from-indigo-400 to-purple-400 h-2 rounded-full transition-all duration-300"
                          style={{ width: `${value * 10}%` }}
                        />
                      </div>
                    </div>
                  ))}
                </div>
              </div>

              {/* Daily Protocols */}
              <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
                {['morning', 'midday', 'evening'].map((timeSlot) => {
                  const protocol = getDailyProtocol(currentDay, userLevel)[timeSlot];
                  const isCompleted = completedProtocols[timeSlot];
                  
                  return (
                    <div key={timeSlot} className={`rounded-xl p-6 transition-all duration-300 ${
                      isCompleted 
                        ? 'bg-emerald-900/60 border-2 border-emerald-400/60 backdrop-blur-sm' 
                        : 'bg-slate-800/60 border-2 border-purple-500/30 hover:border-indigo-400/60 backdrop-blur-sm'
                    } shadow-lg`}>
                      <div className="flex items-center justify-between mb-4">
                        <h4 className="text-lg font-semibold capitalize text-indigo-200">{timeSlot} Protocol</h4>
                        {isCompleted ? (
                          <div className="w-8 h-8 bg-emerald-500 rounded-full flex items-center justify-center">
                            <span className="text-white text-sm">✓</span>
                          </div>
                        ) : (
                          <div className="text-indigo-300 text-sm">{protocol.duration}</div>
                        )}
                      </div>
                      
                      <h5 className="font-medium text-purple-300 mb-3">{protocol.title}</h5>
                      
                      <div className="space-y-3">
                        {protocol.practices.map((practice, idx) => (
                          <div key={idx} className="p-3 bg-slate-700/50 rounded-lg border border-purple-500/20">
                            <div className="font-medium text-sm text-indigo-200 mb-1">{practice.name}</div>
                            <div className="text-xs text-purple-200">{practice.instruction}</div>
                          </div>
                        ))}
                      </div>
                      
                      <button
                        onClick={() => setCompletedProtocols(prev => ({...prev, [timeSlot]: !prev[timeSlot]}))}
                        className={`w-full mt-4 py-2 px-4 rounded-lg font-medium transition-all ${
                          isCompleted
                            ? 'bg-emerald-600 text-white'
                            : 'bg-gradient-to-r from-indigo-600 to-purple-600 text-white hover:from-indigo-500 hover:to-purple-500'
                        }`}
                      >
                        {isCompleted ? 'Completed ✨' : 'Begin Protocol'}
                      </button>
                    </div>
                  );
                })}
              </div>

              {/* Coherence Streak & Badges */}
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div className="bg-slate-800/60 rounded-xl shadow-lg p-6 backdrop-blur-sm border border-purple-500/20">
                  <h3 className="text-xl font-semibold mb-4 flex items-center text-indigo-200">
                    <Zap className="mr-2 text-yellow-400" />
                    Coherence Streak
                  </h3>
                  <div className="text-center">
                    <div className="text-4xl font-bold text-yellow-400 mb-2">{coherenceStreak}</div>
                    <div className="text-purple-200">Days of Quantum Consistency</div>
                    <div className="mt-4 flex justify-center space-x-1">
                      {[...Array(7)].map((_, i) => (
                        <div
                          key={i}
                          className={`w-4 h-4 rounded-full ${
                            i < coherenceStreak ? 'bg-yellow-400' : 'bg-slate-600'
                          }`}
                        />
                      ))}
                    </div>
                  </div>
                </div>

                <div className="bg-slate-800/60 rounded-xl shadow-lg p-6 backdrop-blur-sm border border-purple-500/20">
                  <h3 className="text-xl font-semibold mb-4 flex items-center text-indigo-200">
                    <Award className="mr-2 text-indigo-400" />
                    Achievement Badges
                  </h3>
                  <div className="grid grid-cols-2 gap-3">
                    {badges.map((badge) => (
                      <div
                        key={badge.id}
                        className={`p-3 rounded-lg text-center transition-all ${
                          badge.unlocked
                            ? 'bg-gradient-to-r from-indigo-800/60 to-purple-800/60 text-indigo-200 border border-indigo-400/30'
                            : 'bg-slate-700/40 text-slate-400 border border-slate-600/30'
                        }`}
                      >
                        <div className="text-2xl mb-1">
                          {badge.unlocked ? '🏆' : '🔒'}
                        </div>
                        <div className="text-xs font-medium">{badge.name}</div>
                      </div>
                    ))}
                  </div>
                </div>
              </div>
            </div>
          );

          const MiracleLogger = () => {
            const [newMiracle, setNewMiracle] = useState({ type: '', description: '', intensity: 5 });

            const handleLogMiracle = () => {
              if (newMiracle.description.trim()) {
                setMiracleLog(prev => [...prev, {
                  ...newMiracle,
                  date: new Date().toLocaleDateString(),
                  id: Date.now()
                }]);
                setNewMiracle({ type: '', description: '', intensity: 5 });
              }
            };

            return (
              <div className="space-y-6">
                <div className="text-center mb-8">
                  <h2 className="text-3xl font-bold text-indigo-200 mb-2">Quantum Evidence Logger</h2>
                  <p className="text-purple-200">Document your reality shifts and synchronicities</p>
                </div>

                {/* Add New Miracle */}
                <div className="bg-slate-800/60 rounded-xl shadow-lg p-6 backdrop-blur-sm border border-purple-500/20">
                  <h3 className="text-xl font-semibold mb-4 text-indigo-200">Record New Evidence</h3>
                  <div className="space-y-4">
                    <select 
                      value={newMiracle.type}
                      onChange={(e) => setNewMiracle(prev => ({...prev, type: e.target.value}))}
                      className="w-full p-3 border rounded-lg bg-slate-700 border-purple-500/30 text-indigo-200"
                    >
                      <option value="">Select Evidence Type</option>
                      <option value="synchronicity">Synchronicity</option>
                      <option value="manifestation">Manifestation</option>
                      <option value="healing">Healing</option>
                      <option value="insight">Quantum Insight</option>
                      <option value="serendipity">Serendipity</option>
                    </select>
                    
                    <textarea
                      value={newMiracle.description}
                      onChange={(e) => setNewMiracle(prev => ({...prev, description: e.target.value}))}
                      placeholder="Describe the quantum evidence..."
                      className="w-full p-3 border rounded-lg h-24 bg-slate-700 border-purple-500/30 text-indigo-200 placeholder-purple-300"
                    />
                    
                    <div>
                      <label className="block text-sm font-medium mb-2 text-indigo-200">Impact Intensity (1-10)</label>
                      <input
                        type="range"
                        min="1"
                        max="10"
                        value={newMiracle.intensity}
                        onChange={(e) => setNewMiracle(prev => ({...prev, intensity: parseInt(e.target.value)}))}
                        className="w-full"
                      />
                      <div className="text-center text-sm text-purple-200 mt-1">{newMiracle.intensity}/10</div>
                    </div>
                    
                    <button
                      onClick={handleLogMiracle}
                      className="w-full bg-gradient-to-r from-indigo-600 to-purple-600 text-white py-3 rounded-lg font-medium hover:opacity-90 transition-all"
                    >
                      Log Quantum Evidence ✨
                    </button>
                  </div>
                </div>

                {/* Miracle History */}
                <div className="bg-slate-800/60 rounded-xl shadow-lg p-6 backdrop-blur-sm border border-purple-500/20">
                  <h3 className="text-xl font-semibold mb-4 text-indigo-200">Your Quantum Evidence Archive</h3>
                  {miracleLog.length === 0 ? (
                    <div className="text-center text-purple-300 py-8">
                      <Sparkles className="mx-auto w-12 h-12 text-slate-400 mb-2" />
                      <p>Your miracles will appear here as you document them</p>
                    </div>
                  ) : (
                    <div className="space-y-4">
                      {miracleLog.map((miracle) => (
                        <div key={miracle.id} className="p-4 border-l-4 border-indigo-400 bg-indigo-900/30 rounded-r-lg">
                          <div className="flex justify-between items-start mb-2">
                            <span className="font-medium text-indigo-200 capitalize">{miracle.type}</span>
                            <div className="flex items-center space-x-2">
                              <span className="text-sm text-purple-200">{miracle.date}</span>
                              <div className="flex">
                                {[...Array(miracle.intensity)].map((_, i) => (
                                  <Star key={i} className="w-3 h-3 text-yellow-400 fill-current" />
                                ))}
                              </div>
                            </div>
                          </div>
                          <p className="text-purple-200">{miracle.description}</p>
                        </div>
                      ))}
                    </div>
                  )}
                </div>
              </div>
            );
          };

          const QuantumTools = () => (
            <div className="space-y-6">
              <div className="text-center mb-8">
                <h2 className="text-3xl font-bold text-indigo-200 mb-2">Quantum Reality Tools</h2>
                <p className="text-purple-200">Advanced protocols for reality architecture</p>
              </div>

              {/* Frequency Calibrator */}
              <div className="bg-slate-800/60 rounded-xl shadow-lg p-6 backdrop-blur-sm border border-purple-500/20">
                <h3 className="text-xl font-semibold mb-4 flex items-center text-indigo-200">
                  <Brain className="mr-2 text-indigo-400" />
                  Quantum Frequency Calibrator
                </h3>
                <div className="bg-gradient-to-r from-slate-700/60 to-purple-800/60 p-6 rounded-lg border border-purple-500/30">
                  <div className="text-center mb-6">
                    <div className="text-6xl mb-4">🧠</div>
                    <p className="text-lg font-medium text-indigo-200">Schumann Resonance: 7.83 Hz</p>
                    <p className="text-sm text-purple-200">Earth's Natural Frequency</p>
                  </div>
                  
                  <div className="space-y-4">
                    <div>
                      <h4 className="font-medium mb-2 text-indigo-200">Breathing Protocol:</h4>
                      <ul className="text-sm space-y-1 text-purple-200">
                        <li>• Inhale for 4 seconds: Draw quantum potential</li>
                        <li>• Hold for 4 seconds: Compress possibility into matter</li>
                        <li>• Exhale for 6 seconds: Emit your reality frequency</li>
                        <li>• Repeat 7-8 cycles for coherence</li>
                      </ul>
                    </div>
                  </div>
                </div>
              </div>

              {/* Other tools would go here with similar cosmic styling */}
            </div>
          );

          const ProgressView = () => (
            <div className="space-y-6">
              <div className="text-center mb-8">
                <h2 className="text-3xl font-bold text-indigo-200 mb-2">Quantum Evolution Tracking</h2>
                <p className="text-purple-200">Your transformation metrics and timeline</p>
              </div>

              {/* Level Selector */}
              <div className="bg-slate-800/60 rounded-xl shadow-lg p-6 backdrop-blur-sm border border-purple-500/20">
                <h3 className="text-xl font-semibold mb-4 text-indigo-200">Reality Architect Level</h3>
                <div className="flex space-x-4">
                  {['beginner', 'advanced'].map((level) => (
                    <button
                      key={level}
                      onClick={() => setUserLevel(level)}
                      className={`flex-1 py-3 px-6 rounded-lg font-medium transition-all ${
                        userLevel === level
                          ? 'bg-gradient-to-r from-indigo-600 to-purple-600 text-white'
                          : 'bg-slate-700 text-purple-200 hover:bg-slate-600'
                      }`}
                    >
                      {level === 'beginner' ? '🌱 New Architect' : '⚡ Quantum Master'}
                    </button>
                  ))}
                </div>
                <p className="text-sm text-purple-200 mt-2">
                  {userLevel === 'beginner' 
                    ? 'Simplified protocols with guided entry into quantum reality'
                    : 'Advanced techniques for experienced reality architects'
                  }
                </p>
              </div>

              {/* Progress stats */}
              <div className="grid grid-cols-2 gap-4">
                <div className="bg-slate-800/60 rounded-xl shadow-lg p-6 text-center backdrop-blur-sm border border-purple-500/20">
                  <div className="text-3xl font-bold text-indigo-300">{miracleLog.length}</div>
                  <div className="text-sm text-purple-200">Quantum Evidence</div>
                </div>
                <div className="bg-slate-800/60 rounded-xl shadow-lg p-6 text-center backdrop-blur-sm border border-purple-500/20">
                  <div className="text-3xl font-bold text-purple-300">{Math.round(Object.values(quantumScore).reduce((a,b) => a+b, 0)/3 * 10)}%</div>
                  <div className="text-sm text-purple-200">Reality Coherence</div>
                </div>
              </div>
            </div>
          );

          const Navigation = () => (
            <div className="bg-slate-900/95 shadow-lg rounded-t-2xl p-4 backdrop-blur-sm border-t border-purple-500/30">
              <div className="flex justify-around">
                {[
                  { id: 'dashboard', icon: Calendar, label: 'Today' },
                  { id: 'miracles', icon: Sparkles, label: 'Evidence' },
                  { id: 'tools', icon: Brain, label: 'Tools' },
                  { id: 'progress', icon: TrendingUp, label: 'Progress' }
                ].map(({ id, icon: Icon, label }) => (
                  <button
                    key={id}
                    onClick={() => setCurrentView(id)}
                    className={`flex flex-col items-center p-2 rounded-lg transition-all ${
                      currentView === id
                        ? 'text-indigo-300 bg-indigo-900/60'
                        : 'text-slate-400 hover:text-indigo-400'
                    }`}
                  >
                    <Icon className="w-6 h-6 mb-1" />
                    <span className="text-xs">{label}</span>
                  </button>
                ))}
              </div>
            </div>
          );

          const renderCurrentView = () => {
            switch(currentView) {
              case 'dashboard': return <Dashboard />;
              case 'miracles': return <MiracleLogger />;
              case 'tools': return <QuantumTools />;
              case 'progress': return <ProgressView />;
              default: return <Dashboard />;
            }
          };

          return (
            <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-indigo-900">
              {/* Header */}
              <div className="bg-gradient-to-r from-indigo-900 via-purple-800 to-slate-800 text-silver p-4 border-b border-purple-500/30">
                <div className="max-w-4xl mx-auto flex justify-between items-center">
                  <div>
                    <h1 className="text-2xl font-bold text-silver">Quantum Magnetism</h1>
                    <p className="text-indigo-200">Reality Architecture Platform</p>
                  </div>
                  <div className="text-right">
                    <div className="text-sm text-purple-200">Day {currentDay} of 60</div>
                    <div className="text-xs text-indigo-300">Coherence Streak: {coherenceStreak}</div>
                  </div>
                </div>
              </div>

              {/* Main Content */}
              <div className="max-w-4xl mx-auto p-4 pb-20">
                {renderCurrentView()}
              </div>

              {/* Bottom Navigation */}
              <div className="fixed bottom-0 left-0 right-0 max-w-4xl mx-auto">
                <Navigation />
              </div>
            </div>
          );
        };

        ReactDOM.render(<QuantumMagnetismApp />, document.getElementById('root'));
    </script>
</body>
</html>

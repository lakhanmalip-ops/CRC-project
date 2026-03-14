import React, { useState, useEffect } from 'react';
import { 
  Leaf, 
  MapPin, 
  Phone, 
  Mail, 
  ChevronRight, 
  Menu, 
  X, 
  CheckCircle, 
  Activity, 
  Truck, 
  ShoppingBag, 
  Zap,
  Globe,
  Database,
  ArrowRight
} from 'lucide-react';

const App = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [scrolled, setScrolled] = useState(false);

  useEffect(() => {
    const handleScroll = () => {
      setScrolled(window.scrollY > 50);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const services = [
    {
      title: "Technical Advisory",
      desc: "Scientific guidance on crop planning, nutrient management, and sustainable practices.",
      icon: <Activity className="w-8 h-8 text-green-600" />,
      tag: "Knowledge Hub"
    },
    {
      title: "Agri-Diagnostics",
      desc: "Soil testing, water analysis, and pest/disease diagnosis to optimize input application.",
      icon: <Leaf className="w-8 h-8 text-green-600" />,
      tag: "Science-Driven"
    },
    {
      title: "Farm Mechanisation",
      desc: "Custom hiring centers and engineering solutions to reduce labor intensity.",
      icon: <Zap className="w-8 h-8 text-green-600" />,
      tag: "Efficiency"
    },
    {
      title: "Post-Harvest & Cold Chain",
      desc: "Primary processing, grading, and cold storage to extend shelf life and value.",
      icon: <Truck className="w-8 h-8 text-green-600" />,
      tag: "Value Addition"
    },
    {
      title: "Market Linkages",
      desc: "Direct farm-to-commerce channels and real-time market price advisory.",
      icon: <ShoppingBag className="w-8 h-8 text-green-600" />,
      tag: "Commercial Engine"
    },
    {
      title: "Digital Agriculture",
      desc: "Rural information kiosks and data-driven extension services.",
      icon: <Database className="w-8 h-8 text-green-600" />,
      tag: "Information Hub"
    }
  ];

  const NavItem = ({ href, label }) => (
    <a href={href} className="text-gray-700 hover:text-green-600 font-medium transition-colors duration-200">
      {label}
    </a>
  );

  return (
    <div className="min-h-screen bg-white font-sans text-gray-900 overflow-x-hidden">
      {/* Navigation */}
      <nav className={`fixed w-full z-50 transition-all duration-300 ${scrolled ? 'bg-white shadow-md py-3' : 'bg-transparent py-5'}`}>
        <div className="max-w-7xl mx-auto px-6 flex justify-between items-center">
          <div className="flex items-center gap-2">
            <div className="bg-green-600 p-2 rounded-lg">
              <Leaf className="text-white w-6 h-6" />
            </div>
            <span className={`text-xl font-bold tracking-tight ${!scrolled ? 'text-green-900' : 'text-green-800'}`}>
              MANISHA AGRI <span className="text-green-600">SOLUTIONS</span>
            </span>
          </div>

          {/* Desktop Nav */}
          <div className="hidden md:flex items-center gap-8">
            <NavItem href="#about" label="About" />
            <NavItem href="#services" label="Solutions" />
            <NavItem href="#ecosystem" label="Ecosystem" />
            <button className="bg-green-600 text-white px-6 py-2 rounded-full font-semibold hover:bg-green-700 transition-all transform hover:scale-105">
              Contact Us
            </button>
          </div>

          {/* Mobile Toggle */}
          <button className="md:hidden" onClick={() => setIsMenuOpen(!isMenuOpen)}>
            {isMenuOpen ? <X /> : <Menu />}
          </button>
        </div>

        {/* Mobile Menu */}
        {isMenuOpen && (
          <div className="md:hidden bg-white border-t border-gray-100 p-6 flex flex-col gap-4 animate-fadeIn">
            <NavItem href="#about" label="About" />
            <NavItem href="#services" label="Solutions" />
            <NavItem href="#ecosystem" label="Ecosystem" />
            <button className="bg-green-600 text-white px-6 py-3 rounded-xl font-semibold">Get Started</button>
          </div>
        )}
      </nav>

      {/* Hero Section */}
      <section className="relative h-screen flex items-center pt-20">
        <div className="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1500382017468-9049fed747ef?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80')] bg-cover bg-center">
          <div className="absolute inset-0 bg-gradient-to-r from-white via-white/80 to-transparent"></div>
        </div>
        
        <div className="relative max-w-7xl mx-auto px-6 w-full">
          <div className="max-w-2xl">
            <div className="inline-flex items-center gap-2 bg-green-100 text-green-800 px-4 py-1 rounded-full text-sm font-bold mb-6">
              <CheckCircle size={16} />
              ESTABLISHED 2025 | RATNAGIRI
            </div>
            <h1 className="text-5xl md:text-7xl font-extrabold text-gray-900 leading-tight mb-6">
              Bridging <span className="text-green-600">Scientific</span> Agriculture & Field Practice.
            </h1>
            <p className="text-xl text-gray-700 mb-8 leading-relaxed">
              A Comprehensive Agri-Clinic & Agri-Business Centre. We don't just tell farmers what to do; we provide the commercial tools to execute it.
            </p>
            <div className="flex flex-col sm:flex-row gap-4">
              <button className="bg-green-600 text-white px-8 py-4 rounded-xl font-bold text-lg flex items-center justify-center gap-2 hover:bg-green-700 transition-all shadow-lg shadow-green-200">
                Explore Our Solutions <ArrowRight size={20} />
              </button>
              <button className="bg-white text-green-700 border-2 border-green-600 px-8 py-4 rounded-xl font-bold text-lg hover:bg-green-50 transition-all">
                The Ecosystem
              </button>
            </div>
          </div>
        </div>
      </section>

      {/* At a Glance / Stats */}
      <section className="py-20 bg-green-900 text-white">
        <div className="max-w-7xl mx-auto px-6">
          <div className="grid md:grid-cols-4 gap-12 text-center">
            <div>
              <div className="text-4xl font-bold mb-2">Proprietorship</div>
              <div className="text-green-300">Micro Enterprise Entity</div>
            </div>
            <div>
              <div className="text-4xl font-bold mb-2">B.Tech</div>
              <div className="text-green-300">Agriculture Engineering Led</div>
            </div>
            <div>
              <div className="text-4xl font-bold mb-2">2025</div>
              <div className="text-green-300">Founded Year</div>
            </div>
            <div>
              <div className="text-4xl font-bold mb-2">Maharashtra</div>
              <div className="text-green-300">Konkan Region Focus</div>
            </div>
          </div>
        </div>
      </section>

      {/* Founder Section */}
      <section id="about" className="py-24 bg-gray-50">
        <div className="max-w-7xl mx-auto px-6">
          <div className="flex flex-col md:flex-row items-center gap-16">
            <div className="w-full md:w-1/2">
              <div className="relative">
                <div className="absolute -top-4 -left-4 w-24 h-24 bg-green-100 rounded-full -z-10"></div>
                <h2 className="text-4xl font-bold text-gray-900 mb-6">Expert-Led, <br/><span className="text-green-600">Field-Driven Expertise</span></h2>
                <p className="text-lg text-gray-600 mb-6 italic border-l-4 border-green-600 pl-4">
                  "Agriculture requires more than just labour; it demands engineering and science. We bridge the gap between the laboratory and the land with qualified technical intervention."
                </p>
                <div className="space-y-4">
                  <div className="flex items-center gap-3">
                    <div className="bg-white p-2 rounded-lg shadow-sm">
                      <CheckCircle className="text-green-600" size={20} />
                    </div>
                    <span className="font-semibold text-gray-800 tracking-wide uppercase text-sm">Professional Integrity</span>
                  </div>
                  <div className="flex items-center gap-3">
                    <div className="bg-white p-2 rounded-lg shadow-sm">
                      <CheckCircle className="text-green-600" size={20} />
                    </div>
                    <span className="font-semibold text-gray-800 tracking-wide uppercase text-sm">Farmer-Centric Approach</span>
                  </div>
                  <div className="flex items-center gap-3">
                    <div className="bg-white p-2 rounded-lg shadow-sm">
                      <CheckCircle className="text-green-600" size={20} />
                    </div>
                    <span className="font-semibold text-gray-800 tracking-wide uppercase text-sm">Sustainability & Resilience</span>
                  </div>
                </div>
                <div className="mt-8 p-6 bg-white rounded-2xl shadow-xl border border-gray-100 flex items-center gap-4">
                  <div className="w-16 h-16 bg-green-600 rounded-full flex items-center justify-center text-white font-bold text-2xl">DR</div>
                  <div>
                    <div className="font-bold text-xl text-gray-900">Dhanashri Vijay Rane</div>
                    <div className="text-green-600 font-medium">Founder & Proprietor | B.E. (Agri)</div>
                  </div>
                </div>
              </div>
            </div>
            <div className="w-full md:w-1/2 grid grid-cols-2 gap-4">
              <div className="space-y-4">
                <div className="h-64 rounded-2xl bg-[url('https://images.unsplash.com/photo-1523348837708-15d4a09cfac2?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80')] bg-cover bg-center"></div>
                <div className="p-6 bg-green-600 rounded-2xl text-white">
                  <div className="text-2xl font-bold mb-2">Integrated</div>
                  <p className="text-green-100 text-sm">Advisory & Commercial Services for the Konkan region.</p>
                </div>
              </div>
              <div className="space-y-4 pt-8">
                <div className="p-6 bg-white border border-gray-200 rounded-2xl">
                  <div className="text-2xl font-bold text-green-700 mb-2">Dual-Engine</div>
                  <p className="text-gray-600 text-sm">Knowledge Hub + Commercial Engine for total success.</p>
                </div>
                <div className="h-64 rounded-2xl bg-[url('https://images.unsplash.com/photo-1495107336281-689bb1d3bd1a?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80')] bg-cover bg-center"></div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Services Grid */}
      <section id="services" className="py-24">
        <div className="max-w-7xl mx-auto px-6">
          <div className="text-center mb-16">
            <h2 className="text-4xl font-bold text-gray-900 mb-4">A Holistic Ecosystem</h2>
            <p className="text-xl text-gray-600 max-w-2xl mx-auto">We provide a comprehensive range of services designed to increase farm productivity and ensure market stability.</p>
          </div>
          
          <div className="grid md:grid-cols-3 gap-8">
            {services.map((s, idx) => (
              <div key={idx} className="group p-8 bg-white border border-gray-100 rounded-3xl hover:shadow-2xl hover:border-green-100 transition-all duration-300 transform hover:-translate-y-2">
                <div className="bg-green-50 w-16 h-16 rounded-2xl flex items-center justify-center mb-6 group-hover:bg-green-600 group-hover:text-white transition-colors duration-300">
                  {React.cloneElement(s.icon, { className: "w-8 h-8 group-hover:text-white" })}
                </div>
                <div className="text-xs font-bold text-green-600 uppercase tracking-widest mb-2">{s.tag}</div>
                <h3 className="text-2xl font-bold text-gray-900 mb-3">{s.title}</h3>
                <p className="text-gray-600 leading-relaxed mb-6">{s.desc}</p>
                <a href="#" className="inline-flex items-center gap-2 text-green-700 font-bold group-hover:gap-4 transition-all">
                  Learn More <ChevronRight size={18} />
                </a>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Diversification / Allied Section */}
      <section className="py-24 bg-green-50">
        <div className="max-w-7xl mx-auto px-6">
          <div className="bg-white rounded-[3rem] overflow-hidden shadow-2xl flex flex-col md:flex-row">
            <div className="w-full md:w-1/2 p-12 md:p-20 flex flex-col justify-center">
              <h2 className="text-4xl font-bold text-gray-900 mb-6">Resilience through <span className="text-green-600">Diversification</span></h2>
              <p className="text-lg text-gray-600 mb-8">Building diversified income streams beyond traditional cropping through Allied Livelihoods.</p>
              
              <div className="space-y-6">
                {[
                  { title: "Livestock", detail: "Animal health advisory & feed processing." },
                  { title: "Beekeeping", detail: "Apiary support and honey processing units." },
                  { title: "Fisheries", detail: "Hatcheries and fish fingerling production." }
                ].map((item, i) => (
                  <div key={i} className="flex gap-4">
                    <div className="flex-shrink-0 w-8 h-8 rounded-full bg-green-100 text-green-700 flex items-center justify-center font-bold">
                      {i + 1}
                    </div>
                    <div>
                      <h4 className="font-bold text-gray-900">{item.title}</h4>
                      <p className="text-gray-600">{item.detail}</p>
                    </div>
                  </div>
                ))}
              </div>
            </div>
            <div className="w-full md:w-1/2 relative min-h-[400px]">
              <div className="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1595113316349-9fa4eb24f884?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80')] bg-cover bg-center"></div>
              <div className="absolute inset-0 bg-green-900/10"></div>
            </div>
          </div>
        </div>
      </section>

      {/* CTA / Contact */}
      <section id="ecosystem" className="py-24 relative overflow-hidden">
        <div className="absolute top-0 right-0 w-1/3 h-full bg-green-600 -skew-x-12 translate-x-1/2 -z-10 opacity-10"></div>
        <div className="max-w-7xl mx-auto px-6">
          <div className="flex flex-col md:flex-row justify-between items-center gap-12">
            <div className="max-w-xl">
              <h2 className="text-4xl font-bold mb-6">Ready to transform your farming practice?</h2>
              <p className="text-xl text-gray-600 mb-8">Join the Manisha Agri ecosystem. From soil testing to market shelf, we are your engineering partner in growth.</p>
              
              <div className="space-y-4 text-lg">
                <div className="flex items-center gap-4 text-gray-700">
                  <MapPin className="text-green-600" />
                  <span>Chiplun, Ratnagiri, Maharashtra - 415603</span>
                </div>
                <div className="flex items-center gap-4 text-gray-700">
                  <Phone className="text-green-600" />
                  <span>Inquire for Consultations</span>
                </div>
                <div className="flex items-center gap-4 text-gray-700">
                  <CheckCircle className="text-green-600" />
                  <span>UDYAM-MH-28-0085773</span>
                </div>
              </div>
            </div>

            <div className="w-full md:w-1/2 bg-white p-8 rounded-3xl shadow-2xl border border-gray-100">
              <h3 className="text-2xl font-bold mb-6">Contact Us</h3>
              <form className="space-y-4" onSubmit={e => e.preventDefault()}>
                <div className="grid grid-cols-2 gap-4">
                  <div>
                    <label className="block text-sm font-semibold mb-2 text-gray-700">Name</label>
                    <input type="text" className="w-full p-3 bg-gray-50 rounded-xl border border-gray-200 focus:outline-none focus:ring-2 focus:ring-green-600" placeholder="Your Name" />
                  </div>
                  <div>
                    <label className="block text-sm font-semibold mb-2 text-gray-700">Phone</label>
                    <input type="tel" className="w-full p-3 bg-gray-50 rounded-xl border border-gray-200 focus:outline-none focus:ring-2 focus:ring-green-600" placeholder="Number" />
                  </div>
                </div>
                <div>
                  <label className="block text-sm font-semibold mb-2 text-gray-700">Service Interest</label>
                  <select className="w-full p-3 bg-gray-50 rounded-xl border border-gray-200 focus:outline-none focus:ring-2 focus:ring-green-600">
                    <option>Advisory Services</option>
                    <option>Mechanisation Rental</option>
                    <option>Soil/Diagnostic Testing</option>
                    <option>Post-Harvest Processing</option>
                  </select>
                </div>
                <div>
                  <label className="block text-sm font-semibold mb-2 text-gray-700">Message</label>
                  <textarea className="w-full p-3 bg-gray-50 rounded-xl border border-gray-200 focus:outline-none focus:ring-2 focus:ring-green-600 h-32" placeholder="How can we help you?"></textarea>
                </div>
                <button className="w-full py-4 bg-green-600 text-white rounded-xl font-bold hover:bg-green-700 transition-all">Send Inquiry</button>
              </form>
            </div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-gray-900 text-gray-400 py-16 border-t border-gray-800">
        <div className="max-w-7xl mx-auto px-6">
          <div className="grid md:grid-cols-4 gap-12 mb-12">
            <div className="col-span-1 md:col-span-1">
              <div className="flex items-center gap-2 mb-6">
                <div className="bg-green-600 p-1 rounded-md">
                  <Leaf className="text-white w-5 h-5" />
                </div>
                <span className="text-white font-bold text-lg tracking-tight uppercase">Manisha Agri</span>
              </div>
              <p className="text-sm leading-relaxed">
                Empowering the Konkan farming community with scientific agriculture and integrated commercial solutions.
              </p>
            </div>
            <div>
              <h4 className="text-white font-bold mb-6">Quick Links</h4>
              <ul className="space-y-3 text-sm">
                <li><a href="#" className="hover:text-green-400 transition-colors">Home</a></li>
                <li><a href="#about" className="hover:text-green-400 transition-colors">About the Founder</a></li>
                <li><a href="#services" className="hover:text-green-400 transition-colors">Agri-Services</a></li>
                <li><a href="#ecosystem" className="hover:text-green-400 transition-colors">Ecosystem</a></li>
              </ul>
            </div>
            <div>
              <h4 className="text-white font-bold mb-6">Specializations</h4>
              <ul className="space-y-3 text-sm">
                <li>Agri-Engineering</li>
                <li>Horticulture Development</li>
                <li>Beekeeping & Honey</li>
                <li>Cold Chain Logistics</li>
              </ul>
            </div>
            <div>
              <h4 className="text-white font-bold mb-6">Connect</h4>
              <div className="flex gap-4 mb-6">
                <div className="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center hover:bg-green-600 transition-all cursor-pointer">
                  <Globe size={18} />
                </div>
                <div className="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center hover:bg-green-600 transition-all cursor-pointer">
                  <Phone size={18} />
                </div>
                <div className="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center hover:bg-green-600 transition-all cursor-pointer">
                  <Mail size={18} />
                </div>
              </div>
            </div>
          </div>
          <div className="pt-8 border-t border-gray-800 flex flex-col md:flex-row justify-between items-center gap-4 text-xs">
            <p>© 2025 Manisha Agri Solutions. All Rights Reserved. Reg: UDYAM-MH-28-0085773</p>
            <div className="flex gap-8">
              <span>Privacy Policy</span>
              <span>Terms of Service</span>
            </div>
          </div>
        </div>
      </footer>

      <style dangerouslySetInnerHTML={{ __html: `
        @keyframes fadeIn {
          from { opacity: 0; transform: translateY(-10px); }
          to { opacity: 1; transform: translateY(0); }
        }
        .animate-fadeIn {
          animation: fadeIn 0.3s ease-out forwards;
        }
        html {
          scroll-behavior: smooth;
        }
      `}} />
    </div>
  );
};

export default App;

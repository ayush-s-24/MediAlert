<!DOCTYPE html><html><head><meta name="x-poe-datastore-behavior" content="local_only"><meta http-equiv="Content-Security-Policy" content="default-src 'self' 'unsafe-inline' 'unsafe-eval' data: blob: https://cdnjs.cloudflare.com https://cdn.jsdelivr.net https://code.jquery.com https://unpkg.com https://d3js.org https://threejs.org https://cdn.plot.ly https://stackpath.bootstrapcdn.com https://maps.googleapis.com https://cdn.tailwindcss.com https://ajax.googleapis.com https://kit.fontawesome.com https://cdn.datatables.net https://maxcdn.bootstrapcdn.com https://code.highcharts.com https://tako-static-assets-production.s3.amazonaws.com https://www.youtube.com https://fonts.googleapis.com https://fonts.gstatic.com https://pfst.cf2.poecdn.net https://puc.poecdn.net https://i.imgur.com https://wikimedia.org https://*.icons8.com https://*.giphy.com https://picsum.photos https://images.unsplash.com; frame-src 'self' https://www.youtube.com https://trytako.com; child-src 'self'; manifest-src 'self'; worker-src 'self'; upgrade-insecure-requests; block-all-mixed-content;"><meta http-equiv="x-dns-prefetch-control" content="off"><script src="https://puc.poecdn.net/authenticated_preview_page/standard.3ef2c256959faf5a756d.js"></script>
    <meta charset="utf-8">
    <title>medialert</title>
    <meta name="viewport" content="width=device-width,initial-scale=1">
  <script src="https://puc.poecdn.net/authenticated_preview_page/disableWebRTC.9710cebe07429a9e8e06.js"></script><meta name="x-poe-allow-downloads" content="true"><meta name="x-poe-datastore-behavior" content="disabled"><script src="https://puc.poecdn.net/authenticated_preview_page/tw.50ec1b0612bf5b0c30a5.js"></script><script src="https://puc.poecdn.net/authenticated_preview_page/deps.faccd16000d314dc16d5.js"></script><script src="https://puc.poecdn.net/authenticated_preview_page/exports.b0f0f482cdeb5302b0b9.js"></script><script src="https://puc.poecdn.net/authenticated_preview_page/renderer.75c73ae6b4235f62945a.js"></script><script>Object.defineProperty(exports, "__esModule", {value: true}); function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { default: obj }; } function _optionalChain(ops) { let lastAccessLHS = undefined; let value = ops[0]; let i = 1; while (i < ops.length) { const op = ops[i]; const fn = ops[i + 1]; i += 2; if ((op === 'optionalAccess' || op === 'optionalCall') && value == null) { return undefined; } if (op === 'access' || op === 'optionalAccess') { lastAccessLHS = value; value = fn(value); } else if (op === 'call' || op === 'optionalCall') { value = fn((...args) => value.call(lastAccessLHS, ...args)); lastAccessLHS = undefined; } } return value; }var _react = require('react'); var _react2 = _interopRequireDefault(_react);
var _framermotion = require('framer-motion');








var _lucidereact = require('lucide-react');

// ============ MOCK DATA ============
const MOCK_RECALLS = [
  { id: 'R001', medicine: 'Paracetamol 500mg', batch: 'PCM2024A12', mfr: 'Cipla', reason: 'Contamination detected in batch', severity: 'high', date: '2026-05-12', country: 'India', source: 'CDSCO' },
  { id: 'R002', medicine: 'Atorvastatin 20mg', batch: 'ATR891X', mfr: 'Pfizer', reason: 'Mislabeling — incorrect dosage on packaging', severity: 'critical', date: '2026-05-08', country: 'USA', source: 'FDA' },
  { id: 'R003', medicine: 'Metformin 850mg', batch: 'MET2025B7', mfr: 'Sun Pharma', reason: 'NDMA impurity above acceptable limits', severity: 'high', date: '2026-05-03', country: 'India', source: 'CDSCO' },
  { id: 'R004', medicine: 'Amoxicillin 250mg', batch: 'AMX-7741', mfr: 'GSK', reason: 'Stability issue — early degradation', severity: 'medium', date: '2026-04-28', country: 'UK', source: 'MHRA' },
  { id: 'R005', medicine: 'Losartan 50mg', batch: 'LSR4421', mfr: 'Dr. Reddys', reason: 'Packaging defect — moisture exposure', severity: 'medium', date: '2026-04-22', country: 'India', source: 'CDSCO' },
  { id: 'R006', medicine: 'Ibuprofen 400mg', batch: 'IBU-2024X', mfr: 'Novartis', reason: 'Counterfeit batches in circulation', severity: 'critical', date: '2026-04-15', country: 'EU', source: 'EMA' },
];

const VALID_BATCHES = {
  'PFZ2024001': { name: 'Lipitor 20mg', mfr: 'Pfizer', expiry: '2027-08', mfgDate: '2024-08' },
  'GSK891234': { name: 'Augmentin 625', mfr: 'GSK', expiry: '2026-12', mfgDate: '2024-12' },
  'CIP556677': { name: 'Azithral 500', mfr: 'Cipla', expiry: '2027-03', mfgDate: '2025-03' },
  'SUN123ABC': { name: 'Pantop 40', mfr: 'Sun Pharma', expiry: '2027-06', mfgDate: '2025-06' },
};

const SEED_MEDICINES = [
  { id: 1, name: 'Paracetamol 500mg', batch: 'PCM2024A12', mfr: 'Cipla', dose: '1 tablet', frequency: 'Twice daily', times: ['08:00', '20:00'], expiry: '2027-05', stock: 24, color: 'red' },
  { id: 2, name: 'Vitamin D3 60K', batch: 'VTD2025X1', mfr: 'Sun Pharma', dose: '1 capsule', frequency: 'Weekly', times: ['09:00'], expiry: '2027-12', stock: 8, color: 'amber' },
  { id: 3, name: 'Atorvastatin 10mg', batch: 'ATR2025B', mfr: 'Pfizer', dose: '1 tablet', frequency: 'Once daily', times: ['21:00'], expiry: '2027-09', stock: 30, color: 'blue' },
];

// ============ APP CONTEXT ============
const AppContext = _react.createContext.call(void 0, );
const useApp = () => _react.useContext.call(void 0, AppContext);

// ============ MAIN APP ============
 function MediAlertApp() {
  const [view, setView] = _react.useState.call(void 0, 'splash'); // splash | onboard | login | signup | app
  const [tab, setTab] = _react.useState.call(void 0, 'home');
  const [user, setUser] = _react.useState.call(void 0, null);
  const [medicines, setMedicines] = _react.useState.call(void 0, SEED_MEDICINES);
  const [recalls] = _react.useState.call(void 0, MOCK_RECALLS);
  const [notifications, setNotifications] = _react.useState.call(void 0, [
    { id: 1, type: 'recall', title: 'Recall Alert: Paracetamol 500mg', msg: 'A medicine you take has been recalled.', time: '2h ago', read: false },
    { id: 2, type: 'reminder', title: 'Time for Vitamin D3', msg: 'Take 1 capsule with food', time: '5h ago', read: false },
    { id: 3, type: 'success', title: 'Authenticity Verified ✓', msg: 'Lipitor 20mg confirmed genuine', time: '1d ago', read: true },
  ]);
  const [toast, setToast] = _react.useState.call(void 0, null);

  const showToast = (msg, type = 'info') => {
    setToast({ msg, type, id: Date.now() });
    setTimeout(() => setToast(null), 3000);
  };

  // Auto-progress splash
  _react.useEffect.call(void 0, () => {
    if (view === 'splash') {
      const t = setTimeout(() => setView('onboard'), 2200);
      return () => clearTimeout(t);
    }
  }, [view]);

  const ctx = {
    user, setUser, medicines, setMedicines, recalls, notifications, setNotifications,
    tab, setTab, view, setView, showToast,
  };

  return (
    _react2.default.createElement(AppContext.Provider, { value: ctx,}
      , _react2.default.createElement('div', { className: "min-h-screen bg-slate-50 font-sans antialiased"   ,}
        , _react2.default.createElement('div', { className: "max-w-md mx-auto bg-white min-h-screen relative overflow-hidden shadow-2xl"      ,}
          , _react2.default.createElement(_framermotion.AnimatePresence, { mode: "wait",}
            , view === 'splash' && _react2.default.createElement(Splash, { key: "splash",} )
            , view === 'onboard' && _react2.default.createElement(Onboarding, { key: "onboard",} )
            , view === 'login' && _react2.default.createElement(Login, { key: "login",} )
            , view === 'signup' && _react2.default.createElement(Signup, { key: "signup",} )
            , view === 'app' && _react2.default.createElement(MainApp, { key: "app",} )
          )

          /* Toast */
          , _react2.default.createElement(_framermotion.AnimatePresence, null
            , toast && (
              _react2.default.createElement(_framermotion.motion.div, {
                initial: { y: -50, opacity: 0 },
                animate: { y: 0, opacity: 1 },
                exit: { y: -50, opacity: 0 },
                className: "fixed top-4 left-1/2 -translate-x-1/2 z-50 max-w-md w-11/12"      ,}
                , _react2.default.createElement('div', { className: `px-4 py-3 rounded-xl shadow-2xl flex items-center gap-3 backdrop-blur ${
                  toast.type === 'success' ? 'bg-emerald-500 text-white' :
                  toast.type === 'error' ? 'bg-rose-500 text-white' :
                  toast.type === 'warning' ? 'bg-amber-500 text-white' :
                  'bg-slate-900 text-white'
                }`,}
                  , toast.type === 'success' && _react2.default.createElement(_lucidereact.CheckCircle2, { className: "w-5 h-5" ,} )
                  , toast.type === 'error' && _react2.default.createElement(_lucidereact.XCircle, { className: "w-5 h-5" ,} )
                  , toast.type === 'warning' && _react2.default.createElement(_lucidereact.AlertTriangle, { className: "w-5 h-5" ,} )
                  , toast.type === 'info' && _react2.default.createElement(_lucidereact.Info, { className: "w-5 h-5" ,} )
                  , _react2.default.createElement('span', { className: "text-sm font-medium" ,}, toast.msg)
                )
              )
            )
          )
        )
      )
    )
  );
} exports.default = MediAlertApp;

// ============ SPLASH ============
function Splash() {
  return (
    _react2.default.createElement(_framermotion.motion.div, { exit: { opacity: 0 },
      className: "absolute inset-0 bg-gradient-to-br from-blue-600 via-cyan-500 to-blue-700 flex flex-col items-center justify-center text-white"          ,}
      , _react2.default.createElement(_framermotion.motion.div, {
        initial: { scale: 0.5, opacity: 0 },
        animate: { scale: 1, opacity: 1 },
        transition: { type: 'spring', duration: 0.8 },
        className: "relative",}
        , _react2.default.createElement('div', { className: "absolute inset-0 bg-white/30 blur-3xl rounded-full"    ,} )
        , _react2.default.createElement('div', { className: "relative w-24 h-24 rounded-3xl bg-white/20 backdrop-blur-xl border border-white/30 flex items-center justify-center shadow-2xl"           ,}
          , _react2.default.createElement(_lucidereact.Shield, { className: "w-12 h-12 text-white"  , strokeWidth: 2.5,} )
        )
      )
      , _react2.default.createElement(_framermotion.motion.h1, {
        initial: { y: 20, opacity: 0 },
        animate: { y: 0, opacity: 1 },
        transition: { delay: 0.4 },
        className: "text-4xl font-bold mt-6 tracking-tight"   ,}, "MediAlert")
      , _react2.default.createElement(_framermotion.motion.p, {
        initial: { y: 20, opacity: 0 },
        animate: { y: 0, opacity: 1 },
        transition: { delay: 0.6 },
        className: "text-cyan-100 mt-2 text-sm font-medium"   ,}, "Trusted Medicine Safety"  )
      , _react2.default.createElement(_framermotion.motion.div, {
        initial: { opacity: 0 },
        animate: { opacity: 1 },
        transition: { delay: 1.2 },
        className: "absolute bottom-12" ,}
        , _react2.default.createElement(_lucidereact.Loader2, { className: "w-6 h-6 animate-spin text-white/70"   ,} )
      )
    )
  );
}

// ============ ONBOARDING ============
function Onboarding() {
  const { setView } = useApp();
  const [step, setStep] = _react.useState.call(void 0, 0);
  const slides = [
    { icon: _lucidereact.ShieldCheck, color: 'from-emerald-500 to-teal-500', title: 'Verify Authenticity', desc: 'Scan any medicine to instantly check if it\'s genuine. We cross-verify with FDA, EMA, CDSCO and 6+ manufacturers.' },
    { icon: _lucidereact.AlertOctagon, color: 'from-rose-500 to-orange-500', title: 'Real-time Recall Alerts', desc: 'Get notified the moment a medicine in your cabinet is recalled — anywhere in the world.' },
    { icon: _lucidereact.Bell, color: 'from-blue-500 to-cyan-500', title: 'Smart Reminders', desc: 'Never miss a dose. Track refills, expiry dates, and manage medicines for your whole family.' },
  ];
  const slide = slides[step];

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0 }, animate: { opacity: 1 }, exit: { opacity: 0 },
      className: "absolute inset-0 bg-white flex flex-col"    ,}
      , _react2.default.createElement('div', { className: "flex-1 flex flex-col items-center justify-center px-8 text-center"      ,}
        , _react2.default.createElement(_framermotion.AnimatePresence, { mode: "wait",}
          , _react2.default.createElement(_framermotion.motion.div, {
            key: step,
            initial: { x: 30, opacity: 0 },
            animate: { x: 0, opacity: 1 },
            exit: { x: -30, opacity: 0 },
            className: "flex flex-col items-center"  ,}
            , _react2.default.createElement('div', { className: `w-28 h-28 rounded-3xl bg-gradient-to-br ${slide.color} flex items-center justify-center shadow-2xl mb-8`,}
              , _react2.default.createElement(slide.icon, { className: "w-14 h-14 text-white"  , strokeWidth: 2,} )
            )
            , _react2.default.createElement('h2', { className: "text-3xl font-bold text-slate-900 mb-4"   ,}, slide.title)
            , _react2.default.createElement('p', { className: "text-slate-600 leading-relaxed" ,}, slide.desc)
          )
        )
      )
      , _react2.default.createElement('div', { className: "px-8 pb-10" ,}
        , _react2.default.createElement('div', { className: "flex items-center justify-center gap-2 mb-8"    ,}
          , slides.map((_, i) => (
            _react2.default.createElement('div', { key: i, className: `h-2 rounded-full transition-all ${i === step ? 'w-8 bg-blue-600' : 'w-2 bg-slate-200'}`,} )
          ))
        )
        , _react2.default.createElement('div', { className: "flex gap-3" ,}
          , step > 0 && (
            _react2.default.createElement('button', { onClick: () => setStep(step - 1),
              className: "px-5 py-3.5 rounded-2xl bg-slate-100 text-slate-700 font-semibold"     ,}
              , _react2.default.createElement(_lucidereact.ChevronLeft, { className: "w-5 h-5" ,} )
            )
          )
          , _react2.default.createElement('button', {
            onClick: () => step < slides.length - 1 ? setStep(step + 1) : setView('signup'),
            className: "flex-1 py-3.5 rounded-2xl bg-gradient-to-r from-blue-600 to-cyan-500 text-white font-semibold flex items-center justify-center gap-2 shadow-lg shadow-blue-500/30"             ,}
            , step < slides.length - 1 ? 'Continue' : 'Get Started'
            , _react2.default.createElement(_lucidereact.ArrowRight, { className: "w-5 h-5" ,} )
          )
        )
        , _react2.default.createElement('button', { onClick: () => setView('login'),
          className: "w-full mt-3 py-2.5 text-sm text-slate-500 font-medium"     ,}, "Already have an account? "
              , _react2.default.createElement('span', { className: "text-blue-600",}, "Sign in" )
        )
      )
    )
  );
}

// ============ LOGIN ============
function Login() {
  const { setView, setUser, showToast } = useApp();
  const [email, setEmail] = _react.useState.call(void 0, 'demo@medialert.app');
  const [password, setPassword] = _react.useState.call(void 0, 'demo123');
  const [showPwd, setShowPwd] = _react.useState.call(void 0, false);
  const [loading, setLoading] = _react.useState.call(void 0, false);

  const handleLogin = () => {
    if (!email || !password) return showToast('Please fill all fields', 'error');
    setLoading(true);
    setTimeout(() => {
      setUser({ name: 'Alex Morgan', email, avatar: 'AM' });
      setView('app');
      showToast('Welcome back!', 'success');
    }, 900);
  };

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0 }, animate: { opacity: 1 }, exit: { opacity: 0 },
      className: "absolute inset-0 bg-white flex flex-col"    ,}
      , _react2.default.createElement('div', { className: "px-6 pt-12 pb-6"  ,}
        , _react2.default.createElement('button', { onClick: () => setView('onboard'), className: "w-10 h-10 rounded-full bg-slate-100 flex items-center justify-center"      ,}
          , _react2.default.createElement(_lucidereact.ChevronLeft, { className: "w-5 h-5 text-slate-700"  ,} )
        )
      )
      , _react2.default.createElement('div', { className: "flex-1 px-6" ,}
        , _react2.default.createElement('div', { className: "w-16 h-16 rounded-2xl bg-gradient-to-br from-blue-600 to-cyan-500 flex items-center justify-center mb-6 shadow-lg shadow-blue-500/30"           ,}
          , _react2.default.createElement(_lucidereact.Shield, { className: "w-8 h-8 text-white"  ,} )
        )
        , _react2.default.createElement('h2', { className: "text-3xl font-bold text-slate-900 mb-2"   ,}, "Welcome back" )
        , _react2.default.createElement('p', { className: "text-slate-500 mb-8" ,}, "Sign in to continue protecting your health"      )

        , _react2.default.createElement('div', { className: "space-y-4",}
          , _react2.default.createElement('div', null
            , _react2.default.createElement('label', { className: "text-sm font-medium text-slate-700 mb-1.5 block"    ,}, "Email")
            , _react2.default.createElement('div', { className: "relative",}
              , _react2.default.createElement(_lucidereact.Mail, { className: "w-5 h-5 text-slate-400 absolute left-4 top-1/2 -translate-y-1/2"      ,} )
              , _react2.default.createElement('input', { type: "email", value: email, onChange: e => setEmail(e.target.value),
                className: "w-full pl-12 pr-4 py-3.5 rounded-2xl bg-slate-50 border border-slate-200 focus:border-blue-500 focus:bg-white outline-none transition"           ,} )
            )
          )
          , _react2.default.createElement('div', null
            , _react2.default.createElement('label', { className: "text-sm font-medium text-slate-700 mb-1.5 block"    ,}, "Password")
            , _react2.default.createElement('div', { className: "relative",}
              , _react2.default.createElement(_lucidereact.Lock, { className: "w-5 h-5 text-slate-400 absolute left-4 top-1/2 -translate-y-1/2"      ,} )
              , _react2.default.createElement('input', { type: showPwd ? 'text' : 'password', value: password, onChange: e => setPassword(e.target.value),
                className: "w-full pl-12 pr-12 py-3.5 rounded-2xl bg-slate-50 border border-slate-200 focus:border-blue-500 focus:bg-white outline-none transition"           ,} )
              , _react2.default.createElement('button', { onClick: () => setShowPwd(!showPwd), className: "absolute right-4 top-1/2 -translate-y-1/2 text-slate-400"    ,}
                , showPwd ? _react2.default.createElement(_lucidereact.EyeOff, { className: "w-5 h-5" ,} ) : _react2.default.createElement(_lucidereact.Eye, { className: "w-5 h-5" ,} )
              )
            )
          )
          , _react2.default.createElement('button', { className: "text-sm text-blue-600 font-medium"  ,}, "Forgot password?" )
        )
      )
      , _react2.default.createElement('div', { className: "p-6 space-y-3" ,}
        , _react2.default.createElement('button', { onClick: handleLogin, disabled: loading,
          className: "w-full py-3.5 rounded-2xl bg-gradient-to-r from-blue-600 to-cyan-500 text-white font-semibold flex items-center justify-center gap-2 shadow-lg shadow-blue-500/30 disabled:opacity-60"              ,}
          , loading ? _react2.default.createElement(_lucidereact.Loader2, { className: "w-5 h-5 animate-spin"  ,} ) : _react2.default.createElement(_react2.default.Fragment, null, "Sign In "  , _react2.default.createElement(_lucidereact.ArrowRight, { className: "w-5 h-5" ,} ))
        )
        , _react2.default.createElement('p', { className: "text-center text-sm text-slate-500"  ,}, "New here? "
            , _react2.default.createElement('button', { onClick: () => setView('signup'), className: "text-blue-600 font-semibold" ,}, "Create account" )
        )
      )
    )
  );
}

// ============ SIGNUP ============
function Signup() {
  const { setView, setUser, showToast } = useApp();
  const [form, setForm] = _react.useState.call(void 0, { name: '', email: '', password: '' });
  const [loading, setLoading] = _react.useState.call(void 0, false);

  const handleSignup = () => {
    if (!form.name || !form.email || !form.password) return showToast('Please fill all fields', 'error');
    if (form.password.length < 6) return showToast('Password must be 6+ characters', 'error');
    setLoading(true);
    setTimeout(() => {
      setUser({ name: form.name, email: form.email, avatar: form.name.split(' ').map(s => s[0]).join('').slice(0, 2).toUpperCase() });
      setView('app');
      showToast('Account created! Welcome to MediAlert', 'success');
    }, 1000);
  };

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0 }, animate: { opacity: 1 }, exit: { opacity: 0 },
      className: "absolute inset-0 bg-white flex flex-col"    ,}
      , _react2.default.createElement('div', { className: "px-6 pt-12 pb-6"  ,}
        , _react2.default.createElement('button', { onClick: () => setView('onboard'), className: "w-10 h-10 rounded-full bg-slate-100 flex items-center justify-center"      ,}
          , _react2.default.createElement(_lucidereact.ChevronLeft, { className: "w-5 h-5 text-slate-700"  ,} )
        )
      )
      , _react2.default.createElement('div', { className: "flex-1 px-6" ,}
        , _react2.default.createElement('h2', { className: "text-3xl font-bold text-slate-900 mb-2"   ,}, "Create account" )
        , _react2.default.createElement('p', { className: "text-slate-500 mb-8" ,}, "Join thousands keeping their medicine safe"     )
        , _react2.default.createElement('div', { className: "space-y-4",}
          , [
            { k: 'name', label: 'Full Name', icon: _lucidereact.User, type: 'text', ph: 'Alex Morgan' },
            { k: 'email', label: 'Email', icon: _lucidereact.Mail, type: 'email', ph: 'alex@email.com' },
            { k: 'password', label: 'Password', icon: _lucidereact.Lock, type: 'password', ph: '••••••••' },
          ].map(f => (
            _react2.default.createElement('div', { key: f.k,}
              , _react2.default.createElement('label', { className: "text-sm font-medium text-slate-700 mb-1.5 block"    ,}, f.label)
              , _react2.default.createElement('div', { className: "relative",}
                , _react2.default.createElement(f.icon, { className: "w-5 h-5 text-slate-400 absolute left-4 top-1/2 -translate-y-1/2"      ,} )
                , _react2.default.createElement('input', { type: f.type, placeholder: f.ph, value: form[f.k],
                  onChange: e => setForm({ ...form, [f.k]: e.target.value }),
                  className: "w-full pl-12 pr-4 py-3.5 rounded-2xl bg-slate-50 border border-slate-200 focus:border-blue-500 focus:bg-white outline-none transition"           ,} )
              )
            )
          ))
        )
        , _react2.default.createElement('p', { className: "text-xs text-slate-500 mt-4 leading-relaxed"   ,}, "By creating an account, you agree to our "
                  , _react2.default.createElement('span', { className: "text-blue-600",}, "Terms"), " and "  , _react2.default.createElement('span', { className: "text-blue-600",}, "Privacy Policy" ), "."
        )
      )
      , _react2.default.createElement('div', { className: "p-6 space-y-3" ,}
        , _react2.default.createElement('button', { onClick: handleSignup, disabled: loading,
          className: "w-full py-3.5 rounded-2xl bg-gradient-to-r from-blue-600 to-cyan-500 text-white font-semibold flex items-center justify-center gap-2 shadow-lg shadow-blue-500/30 disabled:opacity-60"              ,}
          , loading ? _react2.default.createElement(_lucidereact.Loader2, { className: "w-5 h-5 animate-spin"  ,} ) : _react2.default.createElement(_react2.default.Fragment, null, "Create Account "  , _react2.default.createElement(_lucidereact.ArrowRight, { className: "w-5 h-5" ,} ))
        )
        , _react2.default.createElement('p', { className: "text-center text-sm text-slate-500"  ,}, "Have an account? "
             , _react2.default.createElement('button', { onClick: () => setView('login'), className: "text-blue-600 font-semibold" ,}, "Sign in" )
        )
      )
    )
  );
}

// ============ MAIN APP ============
function MainApp() {
  const { tab } = useApp();
  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0 }, animate: { opacity: 1 }, exit: { opacity: 0 },
      className: "absolute inset-0 bg-slate-50 flex flex-col"    ,}
      , _react2.default.createElement('div', { className: "flex-1 overflow-y-auto pb-20"  ,}
        , _react2.default.createElement(_framermotion.AnimatePresence, { mode: "wait",}
          , tab === 'home' && _react2.default.createElement(HomeTab, { key: "home",} )
          , tab === 'verify' && _react2.default.createElement(VerifyTab, { key: "verify",} )
          , tab === 'medicines' && _react2.default.createElement(MedicinesTab, { key: "meds",} )
          , tab === 'recalls' && _react2.default.createElement(RecallsTab, { key: "recalls",} )
          , tab === 'profile' && _react2.default.createElement(ProfileTab, { key: "profile",} )
        )
      )
      , _react2.default.createElement(BottomNav, null )
    )
  );
}

// ============ HOME TAB ============
function HomeTab() {
  const { user, medicines, recalls, notifications, setTab } = useApp();
  const myRecalls = _react.useMemo.call(void 0, () =>
    recalls.filter(r => medicines.some(m => m.name.split(' ')[0].toLowerCase() === r.medicine.split(' ')[0].toLowerCase())),
    [recalls, medicines]);
  const unreadCount = notifications.filter(n => !n.read).length;
  const lowStock = medicines.filter(m => m.stock < 10);

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0, y: 10 }, animate: { opacity: 1, y: 0 },}
      /* Header */
      , _react2.default.createElement('div', { className: "bg-gradient-to-br from-blue-600 via-cyan-500 to-blue-700 px-5 pt-12 pb-24 rounded-b-3xl relative overflow-hidden"         ,}
        , _react2.default.createElement('div', { className: "absolute inset-0 opacity-20"  ,}
          , _react2.default.createElement('div', { className: "absolute top-0 right-0 w-64 h-64 bg-white rounded-full blur-3xl"       ,} )
        )
        , _react2.default.createElement('div', { className: "relative flex items-center justify-between"   ,}
          , _react2.default.createElement('div', null
            , _react2.default.createElement('p', { className: "text-cyan-100 text-sm" ,}, "Hello,")
            , _react2.default.createElement('h2', { className: "text-white text-2xl font-bold"  ,}, _optionalChain([user, 'optionalAccess', _2 => _2.name, 'optionalAccess', _3 => _3.split, 'call', _4 => _4(' '), 'access', _5 => _5[0]]), " 👋" )
          )
          , _react2.default.createElement('button', { className: "relative w-11 h-11 rounded-2xl bg-white/20 backdrop-blur flex items-center justify-center"        ,}
            , _react2.default.createElement(_lucidereact.Bell, { className: "w-5 h-5 text-white"  ,} )
            , unreadCount > 0 && (
              _react2.default.createElement('span', { className: "absolute -top-1 -right-1 w-5 h-5 rounded-full bg-rose-500 text-white text-xs font-bold flex items-center justify-center border-2 border-blue-600"              ,}
                , unreadCount
              )
            )
          )
        )
        , _react2.default.createElement('p', { className: "relative text-cyan-50 text-sm mt-6 font-medium flex items-center gap-2"       ,}
          , _react2.default.createElement(_lucidereact.ShieldCheck, { className: "w-4 h-4" ,} ), " Your medicine cabinet is being monitored"
        )
      )

      /* Quick stats */
      , _react2.default.createElement('div', { className: "px-5 -mt-16 relative"  ,}
        , _react2.default.createElement('div', { className: "grid grid-cols-3 gap-3"  ,}
          , [
            { label: 'Medicines', value: medicines.length, icon: _lucidereact.Pill, color: 'from-blue-500 to-cyan-500' },
            { label: 'Recalls', value: myRecalls.length, icon: _lucidereact.AlertOctagon, color: 'from-rose-500 to-orange-500' },
            { label: 'Low stock', value: lowStock.length, icon: _lucidereact.TrendingUp, color: 'from-amber-500 to-yellow-500' },
          ].map(s => (
            _react2.default.createElement('div', { key: s.label, className: "bg-white rounded-2xl p-4 shadow-lg border border-slate-100"     ,}
              , _react2.default.createElement('div', { className: `w-9 h-9 rounded-xl bg-gradient-to-br ${s.color} flex items-center justify-center mb-2`,}
                , _react2.default.createElement(s.icon, { className: "w-4 h-4 text-white"  ,} )
              )
              , _react2.default.createElement('p', { className: "text-2xl font-bold text-slate-900"  ,}, s.value)
              , _react2.default.createElement('p', { className: "text-xs text-slate-500" ,}, s.label)
            )
          ))
        )
      )

      /* Quick verify */
      , _react2.default.createElement('div', { className: "px-5 mt-6" ,}
        , _react2.default.createElement('button', { onClick: () => setTab('verify'),
          className: "w-full p-5 rounded-3xl bg-gradient-to-br from-emerald-500 to-teal-500 text-white shadow-xl shadow-emerald-500/30 flex items-center gap-4"           ,}
          , _react2.default.createElement('div', { className: "w-14 h-14 rounded-2xl bg-white/20 backdrop-blur flex items-center justify-center"       ,}
            , _react2.default.createElement(_lucidereact.Scan, { className: "w-7 h-7" ,} )
          )
          , _react2.default.createElement('div', { className: "flex-1 text-left" ,}
            , _react2.default.createElement('h3', { className: "font-bold text-lg" ,}, "Verify a Medicine"  )
            , _react2.default.createElement('p', { className: "text-emerald-50 text-sm" ,}, "Scan or enter batch number"    )
          )
          , _react2.default.createElement(_lucidereact.ArrowRight, { className: "w-6 h-6" ,} )
        )
      )

      /* Critical alerts */
      , myRecalls.length > 0 && (
        _react2.default.createElement('div', { className: "px-5 mt-6" ,}
          , _react2.default.createElement('div', { className: "flex items-center justify-between mb-3"   ,}
            , _react2.default.createElement('h3', { className: "font-bold text-slate-900 flex items-center gap-2"    ,}
              , _react2.default.createElement(_lucidereact.AlertOctagon, { className: "w-5 h-5 text-rose-500"  ,} ), " Action Required"
            )
            , _react2.default.createElement('button', { onClick: () => setTab('recalls'), className: "text-sm text-blue-600 font-medium"  ,}, "View all" )
          )
          , myRecalls.slice(0, 1).map(r => (
            _react2.default.createElement('div', { key: r.id, className: "p-4 rounded-2xl bg-gradient-to-br from-rose-50 to-orange-50 border border-rose-200"      ,}
              , _react2.default.createElement('div', { className: "flex items-start gap-3"  ,}
                , _react2.default.createElement('div', { className: "w-10 h-10 rounded-xl bg-rose-500 flex items-center justify-center flex-shrink-0"       ,}
                  , _react2.default.createElement(_lucidereact.AlertOctagon, { className: "w-5 h-5 text-white"  ,} )
                )
                , _react2.default.createElement('div', { className: "flex-1",}
                  , _react2.default.createElement('p', { className: "font-bold text-slate-900" ,}, r.medicine)
                  , _react2.default.createElement('p', { className: "text-sm text-slate-600 mt-0.5"  ,}, r.reason)
                  , _react2.default.createElement('div', { className: "flex items-center gap-2 mt-2"   ,}
                    , _react2.default.createElement('span', { className: "px-2 py-0.5 rounded-md bg-rose-100 text-rose-700 text-xs font-bold uppercase"       ,}, r.severity)
                    , _react2.default.createElement('span', { className: "text-xs text-slate-500" ,}, "Batch: " , r.batch)
                  )
                )
              )
            )
          ))
        )
      )

      /* Today's reminders */
      , _react2.default.createElement('div', { className: "px-5 mt-6" ,}
        , _react2.default.createElement('div', { className: "flex items-center justify-between mb-3"   ,}
          , _react2.default.createElement('h3', { className: "font-bold text-slate-900 flex items-center gap-2"    ,}
            , _react2.default.createElement(_lucidereact.Clock, { className: "w-5 h-5 text-blue-500"  ,} ), " Today's Schedule"
          )
          , _react2.default.createElement('button', { onClick: () => setTab('medicines'), className: "text-sm text-blue-600 font-medium"  ,}, "All meds" )
        )
        , _react2.default.createElement('div', { className: "space-y-2",}
          , medicines.slice(0, 3).map(m => (
            _react2.default.createElement('div', { key: m.id, className: "p-4 rounded-2xl bg-white border border-slate-100 flex items-center gap-3"       ,}
              , _react2.default.createElement('div', { className: `w-12 h-12 rounded-xl flex items-center justify-center ${
                m.color === 'red' ? 'bg-red-100 text-red-600' :
                m.color === 'amber' ? 'bg-amber-100 text-amber-600' :
                'bg-blue-100 text-blue-600'
              }`,}
                , _react2.default.createElement(_lucidereact.Pill, { className: "w-6 h-6" ,} )
              )
              , _react2.default.createElement('div', { className: "flex-1",}
                , _react2.default.createElement('p', { className: "font-semibold text-slate-900" ,}, m.name)
                , _react2.default.createElement('p', { className: "text-xs text-slate-500" ,}, m.dose, " • "  , m.frequency)
              )
              , _react2.default.createElement('div', { className: "text-right",}
                , _react2.default.createElement('p', { className: "font-bold text-slate-900" ,}, m.times[0])
                , _react2.default.createElement('p', { className: "text-xs text-slate-500" ,}, m.stock, " left" )
              )
            )
          ))
        )
      )

      /* Tip */
      , _react2.default.createElement('div', { className: "px-5 mt-6 mb-6"  ,}
        , _react2.default.createElement('div', { className: "p-4 rounded-2xl bg-gradient-to-br from-blue-50 to-cyan-50 border border-blue-100 flex gap-3"        ,}
          , _react2.default.createElement(_lucidereact.Sparkles, { className: "w-5 h-5 text-blue-600 flex-shrink-0 mt-0.5"    ,} )
          , _react2.default.createElement('div', null
            , _react2.default.createElement('p', { className: "text-sm font-semibold text-slate-900"  ,}, "Health Tip" )
            , _react2.default.createElement('p', { className: "text-xs text-slate-600 mt-1"  ,}, "Always check the batch number on your medicine packaging before consumption. Counterfeit drugs are a global concern."                )
          )
        )
      )
    )
  );
}

// ============ VERIFY TAB ============
function VerifyTab() {
  const { showToast } = useApp();
  const [batch, setBatch] = _react.useState.call(void 0, '');
  const [scanning, setScanning] = _react.useState.call(void 0, false);
  const [result, setResult] = _react.useState.call(void 0, null);
  const [history, setHistory] = _react.useState.call(void 0, [
    { batch: 'PFZ2024001', name: 'Lipitor 20mg', verdict: 'genuine', date: '2 days ago' },
    { batch: 'XYZ999BAD', name: 'Unknown', verdict: 'suspicious', date: '1 week ago' },
  ]);

  const verify = (b) => {
    if (!b.trim()) return showToast('Enter batch number', 'error');
    setScanning(true);
    setResult(null);

    setTimeout(() => {
      const code = b.trim().toUpperCase();
      const valid = VALID_BATCHES[code];
      const recalled = MOCK_RECALLS.find(r => r.batch.toUpperCase() === code);

      let res;
      if (recalled) {
        res = {
          status: 'recalled', batch: code,
          name: recalled.medicine, mfr: recalled.mfr,
          message: 'RECALLED — Do not use!',
          details: recalled.reason,
          sources: ['CDSCO', 'FDA', 'Manufacturer'],
        };
      } else if (valid) {
        res = {
          status: 'genuine', batch: code,
          name: valid.name, mfr: valid.mfr,
          mfgDate: valid.mfgDate, expiry: valid.expiry,
          message: 'Genuine & Safe',
          details: 'Verified across 4 regulatory databases',
          sources: ['FDA', 'CDSCO', 'Manufacturer', 'EMA'],
        };
      } else {
        res = {
          status: 'unknown', batch: code,
          name: 'Not Found',
          message: 'Batch not found in any database',
          details: 'This may be counterfeit. Please consult your pharmacist.',
          sources: [],
        };
      }
      setResult(res);
      setHistory([{ batch: code, name: res.name, verdict: res.status === 'genuine' ? 'genuine' : res.status === 'recalled' ? 'recalled' : 'suspicious', date: 'Just now' }, ...history.slice(0, 4)]);
      setScanning(false);
    }, 1800);
  };

  const tryBatches = ['PFZ2024001', 'PCM2024A12', 'XYZ999BAD'];

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0, y: 10 }, animate: { opacity: 1, y: 0 }, className: "px-5 pt-12 pb-6"  ,}
      , _react2.default.createElement('h1', { className: "text-2xl font-bold text-slate-900 mb-1"   ,}, "Verify Medicine" )
      , _react2.default.createElement('p', { className: "text-slate-500 mb-6" ,}, "Check authenticity instantly"  )

      /* Scan box */
      , _react2.default.createElement('div', { className: "rounded-3xl bg-gradient-to-br from-blue-600 to-cyan-500 p-6 text-white mb-5 shadow-lg shadow-blue-500/30"        ,}
        , _react2.default.createElement('div', { className: "flex items-center gap-2 mb-4"   ,}
          , _react2.default.createElement(_lucidereact.Scan, { className: "w-5 h-5" ,} )
          , _react2.default.createElement('span', { className: "font-semibold",}, "Scan Barcode / QR"   )
        )
        , _react2.default.createElement('button', {
          onClick: () => { setScanning(true); setTimeout(() => { verify(tryBatches[Math.floor(Math.random()*tryBatches.length)]); }, 1200); },
          className: "w-full aspect-video rounded-2xl bg-white/10 backdrop-blur border-2 border-dashed border-white/40 flex flex-col items-center justify-center gap-2 active:scale-95 transition"              ,}
          , scanning ? (
            _react2.default.createElement(_react2.default.Fragment, null
              , _react2.default.createElement(_lucidereact.Loader2, { className: "w-10 h-10 animate-spin"  ,} )
              , _react2.default.createElement('span', { className: "text-sm",}, "Scanning...")
            )
          ) : (
            _react2.default.createElement(_react2.default.Fragment, null
              , _react2.default.createElement(_lucidereact.Camera, { className: "w-10 h-10" ,} )
              , _react2.default.createElement('span', { className: "text-sm font-medium" ,}, "Tap to simulate scan"   )
            )
          )
        )
      )

      /* Manual entry */
      , _react2.default.createElement('div', { className: "mb-5",}
        , _react2.default.createElement('label', { className: "text-sm font-medium text-slate-700 mb-2 block"    ,}, "Or enter batch number"   )
        , _react2.default.createElement('div', { className: "flex gap-2" ,}
          , _react2.default.createElement('input', { value: batch, onChange: e => setBatch(e.target.value.toUpperCase()),
            placeholder: "e.g., PFZ2024001" ,
            className: "flex-1 px-4 py-3.5 rounded-2xl bg-slate-100 border border-slate-200 focus:border-blue-500 focus:bg-white outline-none font-mono text-sm transition"            ,} )
          , _react2.default.createElement('button', { onClick: () => verify(batch), disabled: scanning,
            className: "px-5 rounded-2xl bg-blue-600 text-white font-semibold disabled:opacity-50"     ,}
            , scanning ? _react2.default.createElement(_lucidereact.Loader2, { className: "w-5 h-5 animate-spin"  ,} ) : 'Verify'
          )
        )
        , _react2.default.createElement('div', { className: "flex flex-wrap gap-2 mt-3"   ,}
          , tryBatches.map(b => (
            _react2.default.createElement('button', { key: b, onClick: () => { setBatch(b); verify(b); },
              className: "text-xs px-3 py-1.5 rounded-full bg-slate-100 text-slate-700 font-mono"      ,}, "Try: " , b)
          ))
        )
      )

      /* Result */
      , _react2.default.createElement(_framermotion.AnimatePresence, null
        , result && _react2.default.createElement(VerifyResult, { result: result,} )
      )

      /* History */
      , !result && (
        _react2.default.createElement('div', { className: "mt-6",}
          , _react2.default.createElement('h3', { className: "font-bold text-slate-900 mb-3 flex items-center gap-2"     ,}
            , _react2.default.createElement(_lucidereact.Clock, { className: "w-4 h-4" ,} ), " Recent Checks"
          )
          , _react2.default.createElement('div', { className: "space-y-2",}
            , history.map((h, i) => (
              _react2.default.createElement('div', { key: i, className: "p-3 rounded-2xl bg-white border border-slate-100 flex items-center gap-3"       ,}
                , _react2.default.createElement('div', { className: `w-9 h-9 rounded-xl flex items-center justify-center ${
                  h.verdict === 'genuine' ? 'bg-emerald-100 text-emerald-600' :
                  h.verdict === 'recalled' ? 'bg-rose-100 text-rose-600' :
                  'bg-amber-100 text-amber-600'
                }`,}
                  , h.verdict === 'genuine' ? _react2.default.createElement(_lucidereact.ShieldCheck, { className: "w-5 h-5" ,} ) :
                   h.verdict === 'recalled' ? _react2.default.createElement(_lucidereact.ShieldX, { className: "w-5 h-5" ,} ) :
                   _react2.default.createElement(_lucidereact.ShieldAlert, { className: "w-5 h-5" ,} )
                )
                , _react2.default.createElement('div', { className: "flex-1 min-w-0" ,}
                  , _react2.default.createElement('p', { className: "font-semibold text-slate-900 text-sm truncate"   ,}, h.name)
                  , _react2.default.createElement('p', { className: "text-xs text-slate-500 font-mono"  ,}, h.batch)
                )
                , _react2.default.createElement('p', { className: "text-xs text-slate-400" ,}, h.date)
              )
            ))
          )
        )
      )
    )
  );
}

function VerifyResult({ result }) {
  const cfg = {
    genuine:  { bg: 'from-emerald-500 to-teal-500', icon: _lucidereact.ShieldCheck, text: 'GENUINE' },
    recalled: { bg: 'from-rose-500 to-orange-500',   icon: _lucidereact.ShieldX,     text: 'RECALLED' },
    unknown:  { bg: 'from-amber-500 to-yellow-500',  icon: _lucidereact.ShieldAlert, text: 'UNKNOWN'  },
  }[result.status];
  const Icon = cfg.icon;

  return (
    _react2.default.createElement(_framermotion.motion.div, {
      initial: { scale: 0.9, opacity: 0 },
      animate: { scale: 1, opacity: 1 },
      exit: { scale: 0.9, opacity: 0 },
      className: `rounded-3xl bg-gradient-to-br ${cfg.bg} p-6 text-white shadow-2xl`,}
      , _react2.default.createElement('div', { className: "flex items-center gap-3 mb-4"   ,}
        , _react2.default.createElement('div', { className: "w-14 h-14 rounded-2xl bg-white/20 backdrop-blur flex items-center justify-center"       ,}
          , _react2.default.createElement(Icon, { className: "w-8 h-8" ,} )
        )
        , _react2.default.createElement('div', null
          , _react2.default.createElement('p', { className: "text-xs uppercase font-bold tracking-wider opacity-80"    ,}, cfg.text)
          , _react2.default.createElement('h3', { className: "text-xl font-bold" ,}, result.message)
        )
      )
      , _react2.default.createElement('div', { className: "bg-white/15 backdrop-blur rounded-2xl p-4 space-y-2"    ,}
        , _react2.default.createElement(Row, { label: "Medicine", val: result.name,} )
        , result.mfr && _react2.default.createElement(Row, { label: "Manufacturer", val: result.mfr,} )
        , _react2.default.createElement(Row, { label: "Batch", val: _react2.default.createElement('span', { className: "font-mono",}, result.batch),} )
        , result.mfgDate && _react2.default.createElement(Row, { label: "Mfg Date" , val: result.mfgDate,} )
        , result.expiry && _react2.default.createElement(Row, { label: "Expires", val: result.expiry,} )
      )
      , _react2.default.createElement('p', { className: "text-sm opacity-90 mt-3"  ,}, result.details)
      , _optionalChain([result, 'access', _6 => _6.sources, 'optionalAccess', _7 => _7.length]) > 0 && (
        _react2.default.createElement('div', { className: "flex flex-wrap gap-1.5 mt-3"   ,}
          , result.sources.map(s => (
            _react2.default.createElement('span', { key: s, className: "px-2 py-1 rounded-md bg-white/20 text-xs font-medium"     ,}, s, " ✓" )
          ))
        )
      )
    )
  );
}

const Row = ({ label, val }) => (
  _react2.default.createElement('div', { className: "flex items-center justify-between text-sm"   ,}
    , _react2.default.createElement('span', { className: "opacity-80",}, label)
    , _react2.default.createElement('span', { className: "font-semibold",}, val)
  )
);

// ============ MEDICINES TAB ============
function MedicinesTab() {
  const { medicines, setMedicines, showToast } = useApp();
  const [showAdd, setShowAdd] = _react.useState.call(void 0, false);
  const [search, setSearch] = _react.useState.call(void 0, '');

  const filtered = medicines.filter(m => m.name.toLowerCase().includes(search.toLowerCase()));

  const remove = (id) => {
    setMedicines(medicines.filter(m => m.id !== id));
    showToast('Medicine removed', 'info');
  };

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0, y: 10 }, animate: { opacity: 1, y: 0 }, className: "px-5 pt-12 pb-6"  ,}
      , _react2.default.createElement('div', { className: "flex items-center justify-between mb-1"   ,}
        , _react2.default.createElement('h1', { className: "text-2xl font-bold text-slate-900"  ,}, "My Medicines" )
        , _react2.default.createElement('button', { onClick: () => setShowAdd(true),
          className: "w-10 h-10 rounded-2xl bg-blue-600 text-white flex items-center justify-center shadow-lg shadow-blue-500/30"         ,}
          , _react2.default.createElement(_lucidereact.Plus, { className: "w-5 h-5" ,} )
        )
      )
      , _react2.default.createElement('p', { className: "text-slate-500 mb-5" ,}, medicines.length, " medicines tracked"  )

      , _react2.default.createElement('div', { className: "relative mb-5" ,}
        , _react2.default.createElement(_lucidereact.Search, { className: "w-5 h-5 text-slate-400 absolute left-4 top-1/2 -translate-y-1/2"      ,} )
        , _react2.default.createElement('input', { value: search, onChange: e => setSearch(e.target.value), placeholder: "Search medicines..." ,
          className: "w-full pl-11 pr-4 py-3 rounded-2xl bg-slate-100 outline-none focus:bg-white focus:border-blue-500 border border-transparent transition"           ,} )
      )

      , filtered.length === 0 ? (
        _react2.default.createElement('div', { className: "text-center py-16" ,}
          , _react2.default.createElement(_lucidereact.Pill, { className: "w-12 h-12 text-slate-300 mx-auto mb-3"    ,} )
          , _react2.default.createElement('p', { className: "text-slate-500",}, "No medicines yet"  )
          , _react2.default.createElement('button', { onClick: () => setShowAdd(true), className: "mt-4 px-5 py-2.5 rounded-2xl bg-blue-600 text-white font-medium text-sm"       ,}, "Add your first medicine"

          )
        )
      ) : (
        _react2.default.createElement('div', { className: "space-y-3",}
          , filtered.map(m => _react2.default.createElement(MedicineCard, { key: m.id, med: m, onRemove: () => remove(m.id),} ))
        )
      )

      , _react2.default.createElement(_framermotion.AnimatePresence, null
        , showAdd && _react2.default.createElement(AddMedicineSheet, { onClose: () => setShowAdd(false),} )
      )
    )
  );
}

function MedicineCard({ med, onRemove }) {
  const [open, setOpen] = _react.useState.call(void 0, false);
  const colorClasses = {
    red: 'bg-red-100 text-red-600',
    amber: 'bg-amber-100 text-amber-600',
    blue: 'bg-blue-100 text-blue-600',
  };

  return (
    _react2.default.createElement(_framermotion.motion.div, { layout: true, className: "rounded-2xl bg-white border border-slate-100 overflow-hidden"    ,}
      , _react2.default.createElement('button', { onClick: () => setOpen(!open), className: "w-full p-4 flex items-center gap-3 text-left"     ,}
        , _react2.default.createElement('div', { className: `w-12 h-12 rounded-xl flex items-center justify-center ${colorClasses[med.color] || 'bg-slate-100 text-slate-600'}`,}
          , _react2.default.createElement(_lucidereact.Pill, { className: "w-6 h-6" ,} )
        )
        , _react2.default.createElement('div', { className: "flex-1 min-w-0" ,}
          , _react2.default.createElement('p', { className: "font-semibold text-slate-900 truncate"  ,}, med.name)
          , _react2.default.createElement('p', { className: "text-xs text-slate-500" ,}, med.dose, " • "  , med.frequency)
        )
        , _react2.default.createElement('div', { className: "text-right",}
          , _react2.default.createElement('p', { className: `text-sm font-bold ${med.stock < 10 ? 'text-amber-600' : 'text-slate-700'}`,}, med.stock)
          , _react2.default.createElement('p', { className: "text-xs text-slate-400" ,}, "left")
        )
      )
      , _react2.default.createElement(_framermotion.AnimatePresence, null
        , open && (
          _react2.default.createElement(_framermotion.motion.div, { initial: { height: 0 }, animate: { height: 'auto' }, exit: { height: 0 }, className: "overflow-hidden",}
            , _react2.default.createElement('div', { className: "px-4 pb-4 pt-1 border-t border-slate-100 space-y-3"     ,}
              , _react2.default.createElement('div', { className: "grid grid-cols-2 gap-2 text-sm"   ,}
                , _react2.default.createElement(Info2, { label: "Manufacturer", val: med.mfr,} )
                , _react2.default.createElement(Info2, { label: "Batch", val: med.batch, mono: true,} )
                , _react2.default.createElement(Info2, { label: "Expiry", val: med.expiry,} )
                , _react2.default.createElement(Info2, { label: "Times", val: med.times.join(', '),} )
              )
              , _react2.default.createElement('div', { className: "flex gap-2" ,}
                , _react2.default.createElement('button', { className: "flex-1 py-2.5 rounded-xl bg-blue-50 text-blue-700 font-medium text-sm flex items-center justify-center gap-1.5"          ,}
                  , _react2.default.createElement(_lucidereact.Edit3, { className: "w-4 h-4" ,} ), " Edit"
                )
                , _react2.default.createElement('button', { onClick: onRemove,
                  className: "flex-1 py-2.5 rounded-xl bg-rose-50 text-rose-700 font-medium text-sm flex items-center justify-center gap-1.5"          ,}
                  , _react2.default.createElement(_lucidereact.Trash2, { className: "w-4 h-4" ,} ), " Remove"
                )
              )
            )
          )
        )
      )
    )
  );
}

const Info2 = ({ label, val, mono }) => (
  _react2.default.createElement('div', { className: "p-2.5 rounded-xl bg-slate-50"  ,}
    , _react2.default.createElement('p', { className: "text-xs text-slate-500" ,}, label)
    , _react2.default.createElement('p', { className: `text-sm font-semibold text-slate-900 ${mono ? 'font-mono' : ''}`,}, val)
  )
);

function AddMedicineSheet({ onClose }) {
  const { medicines, setMedicines, showToast } = useApp();
  const [form, setForm] = _react.useState.call(void 0, { name: '', batch: '', mfr: '', dose: '1 tablet', frequency: 'Once daily', expiry: '' });

  const submit = () => {
    if (!form.name) return showToast('Name is required', 'error');
    setMedicines([...medicines, {
      ...form,
      id: Date.now(),
      times: ['09:00'],
      stock: 30,
      color: ['red', 'amber', 'blue'][Math.floor(Math.random()*3)],
    }]);
    showToast('Medicine added!', 'success');
    onClose();
  };

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0 }, animate: { opacity: 1 }, exit: { opacity: 0 },
      className: "fixed inset-0 bg-black/50 flex items-end z-40 max-w-md mx-auto"       ,
      onClick: onClose,}
      , _react2.default.createElement(_framermotion.motion.div, {
        initial: { y: '100%' }, animate: { y: 0 }, exit: { y: '100%' },
        transition: { type: 'spring', damping: 30 },
        onClick: e => e.stopPropagation(),
        className: "w-full bg-white rounded-t-3xl p-6 max-h-screen overflow-y-auto"     ,}
        , _react2.default.createElement('div', { className: "w-12 h-1 bg-slate-200 rounded-full mx-auto mb-4"     ,} )
        , _react2.default.createElement('h3', { className: "text-xl font-bold mb-1"  ,}, "Add Medicine" )
        , _react2.default.createElement('p', { className: "text-slate-500 text-sm mb-5"  ,}, "Track a new medicine"   )
        , _react2.default.createElement('div', { className: "space-y-3",}
          , [
            { k: 'name', label: 'Name *', ph: 'e.g., Paracetamol 500mg' },
            { k: 'batch', label: 'Batch Number', ph: 'e.g., PCM2024A12' },
            { k: 'mfr', label: 'Manufacturer', ph: 'e.g., Cipla' },
            { k: 'dose', label: 'Dose', ph: '1 tablet' },
            { k: 'frequency', label: 'Frequency', ph: 'Once daily' },
            { k: 'expiry', label: 'Expiry (YYYY-MM)', ph: '2027-05' },
          ].map(f => (
            _react2.default.createElement('div', { key: f.k,}
              , _react2.default.createElement('label', { className: "text-xs font-medium text-slate-600 mb-1 block"    ,}, f.label)
              , _react2.default.createElement('input', { value: form[f.k], onChange: e => setForm({ ...form, [f.k]: e.target.value }),
                placeholder: f.ph,
                className: "w-full px-4 py-3 rounded-2xl bg-slate-100 outline-none focus:bg-white focus:border-blue-500 border border-transparent"         ,} )
            )
          ))
        )
        , _react2.default.createElement('div', { className: "flex gap-2 mt-5"  ,}
          , _react2.default.createElement('button', { onClick: onClose, className: "flex-1 py-3.5 rounded-2xl bg-slate-100 text-slate-700 font-semibold"     ,}, "Cancel")
          , _react2.default.createElement('button', { onClick: submit, className: "flex-1 py-3.5 rounded-2xl bg-blue-600 text-white font-semibold"     ,}, "Add Medicine" )
        )
      )
    )
  );
}

// ============ RECALLS TAB ============
function RecallsTab() {
  const { recalls } = useApp();
  const [filter, setFilter] = _react.useState.call(void 0, 'all');
  const [selected, setSelected] = _react.useState.call(void 0, null);

  const filtered = filter === 'all' ? recalls : recalls.filter(r => r.severity === filter);

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0, y: 10 }, animate: { opacity: 1, y: 0 }, className: "px-5 pt-12 pb-6"  ,}
      , _react2.default.createElement('h1', { className: "text-2xl font-bold text-slate-900 mb-1"   ,}, "Recall Center" )
      , _react2.default.createElement('p', { className: "text-slate-500 mb-5" ,}, "Live updates from regulators worldwide"    )

      , _react2.default.createElement('div', { className: "flex gap-2 mb-5 overflow-x-auto pb-1"    ,}
        , [
          { k: 'all', label: 'All', count: recalls.length },
          { k: 'critical', label: 'Critical', count: recalls.filter(r => r.severity === 'critical').length },
          { k: 'high', label: 'High', count: recalls.filter(r => r.severity === 'high').length },
          { k: 'medium', label: 'Medium', count: recalls.filter(r => r.severity === 'medium').length },
        ].map(f => (
          _react2.default.createElement('button', { key: f.k, onClick: () => setFilter(f.k),
            className: `px-4 py-2 rounded-full text-sm font-medium whitespace-nowrap transition ${
              filter === f.k ? 'bg-slate-900 text-white' : 'bg-slate-100 text-slate-700'
            }`,}
            , f.label, " " , _react2.default.createElement('span', { className: "opacity-60",}, "(", f.count, ")")
          )
        ))
      )

      , _react2.default.createElement('div', { className: "space-y-3",}
        , filtered.map(r => (
          _react2.default.createElement('button', { key: r.id, onClick: () => setSelected(r),
            className: "w-full p-4 rounded-2xl bg-white border border-slate-100 hover:shadow-md transition text-left"        ,}
            , _react2.default.createElement('div', { className: "flex items-start gap-3"  ,}
              , _react2.default.createElement('div', { className: `w-10 h-10 rounded-xl flex items-center justify-center flex-shrink-0 ${
                r.severity === 'critical' ? 'bg-rose-100 text-rose-600' :
                r.severity === 'high' ? 'bg-orange-100 text-orange-600' :
                'bg-amber-100 text-amber-600'
              }`,}
                , _react2.default.createElement(_lucidereact.AlertOctagon, { className: "w-5 h-5" ,} )
              )
              , _react2.default.createElement('div', { className: "flex-1 min-w-0" ,}
                , _react2.default.createElement('div', { className: "flex items-center justify-between gap-2 mb-1"    ,}
                  , _react2.default.createElement('p', { className: "font-semibold text-slate-900 truncate"  ,}, r.medicine)
                  , _react2.default.createElement(_lucidereact.ChevronRight, { className: "w-4 h-4 text-slate-400 flex-shrink-0"   ,} )
                )
                , _react2.default.createElement('p', { className: "text-xs text-slate-500 line-clamp-2"  ,}, r.reason)
                , _react2.default.createElement('div', { className: "flex items-center gap-2 mt-2 flex-wrap"    ,}
                  , _react2.default.createElement('span', { className: `px-2 py-0.5 rounded-md text-xs font-bold uppercase ${
                    r.severity === 'critical' ? 'bg-rose-100 text-rose-700' :
                    r.severity === 'high' ? 'bg-orange-100 text-orange-700' :
                    'bg-amber-100 text-amber-700'
                  }`,}, r.severity)
                  , _react2.default.createElement('span', { className: "text-xs text-slate-500" ,}, "• " , r.source)
                  , _react2.default.createElement('span', { className: "text-xs text-slate-400" ,}, "• " , r.date)
                )
              )
            )
          )
        ))
      )

      , _react2.default.createElement(_framermotion.AnimatePresence, null
        , selected && _react2.default.createElement(RecallDetail, { recall: selected, onClose: () => setSelected(null),} )
      )
    )
  );
}

function RecallDetail({ recall, onClose }) {
  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0 }, animate: { opacity: 1 }, exit: { opacity: 0 },
      className: "fixed inset-0 bg-black/50 flex items-end z-40 max-w-md mx-auto"       , onClick: onClose,}
      , _react2.default.createElement(_framermotion.motion.div, {
        initial: { y: '100%' }, animate: { y: 0 }, exit: { y: '100%' },
        transition: { type: 'spring', damping: 30 },
        onClick: e => e.stopPropagation(),
        className: "w-full bg-white rounded-t-3xl p-6 max-h-screen overflow-y-auto"     ,}
        , _react2.default.createElement('div', { className: "w-12 h-1 bg-slate-200 rounded-full mx-auto mb-4"     ,} )
        , _react2.default.createElement('div', { className: `p-4 rounded-2xl mb-4 ${
          recall.severity === 'critical' ? 'bg-rose-50' :
          recall.severity === 'high' ? 'bg-orange-50' :
          'bg-amber-50'
        }`,}
          , _react2.default.createElement('div', { className: "flex items-center gap-2 mb-2"   ,}
            , _react2.default.createElement(_lucidereact.AlertOctagon, { className: `w-5 h-5 ${
              recall.severity === 'critical' ? 'text-rose-600' :
              recall.severity === 'high' ? 'text-orange-600' :
              'text-amber-600'
            }`,} )
            , _react2.default.createElement('span', { className: `text-xs font-bold uppercase ${
              recall.severity === 'critical' ? 'text-rose-700' :
              recall.severity === 'high' ? 'text-orange-700' :
              'text-amber-700'
            }`,}, recall.severity, " Severity" )
          )
          , _react2.default.createElement('h3', { className: "text-xl font-bold text-slate-900"  ,}, recall.medicine)
        )

        , _react2.default.createElement('div', { className: "space-y-3",}
          , _react2.default.createElement(DetailRow, { icon: _lucidereact.Package, label: "Manufacturer", val: recall.mfr,} )
          , _react2.default.createElement(DetailRow, { icon: _lucidereact.FileText, label: "Batch Number" , val: recall.batch, mono: true,} )
          , _react2.default.createElement(DetailRow, { icon: _lucidereact.Calendar, label: "Recall Date" , val: recall.date,} )
          , _react2.default.createElement(DetailRow, { icon: _lucidereact.Globe, label: "Country", val: recall.country,} )
          , _react2.default.createElement(DetailRow, { icon: _lucidereact.Shield, label: "Source", val: recall.source,} )
          , _react2.default.createElement('div', { className: "p-4 rounded-2xl bg-slate-50"  ,}
            , _react2.default.createElement('p', { className: "text-xs font-medium text-slate-500 mb-1"   ,}, "Reason for Recall"  )
            , _react2.default.createElement('p', { className: "text-sm text-slate-900" ,}, recall.reason)
          )
        )

        , _react2.default.createElement('div', { className: "bg-blue-50 rounded-2xl p-4 mt-4"   ,}
          , _react2.default.createElement('p', { className: "text-sm font-bold text-blue-900 mb-2"   ,}, "What to do?"  )
          , _react2.default.createElement('ul', { className: "text-sm text-blue-800 space-y-1.5 list-disc list-inside"    ,}
            , _react2.default.createElement('li', null, "Stop using this batch immediately"    )
            , _react2.default.createElement('li', null, "Return to pharmacy for refund/replacement"    )
            , _react2.default.createElement('li', null, "Consult your doctor if you've already used it"       )
            , _react2.default.createElement('li', null, "Report adverse effects to local authorities"     )
          )
        )

        , _react2.default.createElement('div', { className: "flex gap-2 mt-5"  ,}
          , _react2.default.createElement('button', { className: "flex-1 py-3.5 rounded-2xl bg-slate-100 text-slate-700 font-semibold flex items-center justify-center gap-2"         ,}
            , _react2.default.createElement(_lucidereact.Share2, { className: "w-4 h-4" ,} ), " Share"
          )
          , _react2.default.createElement('button', { onClick: onClose, className: "flex-1 py-3.5 rounded-2xl bg-blue-600 text-white font-semibold"     ,}, "Got it" )
        )
      )
    )
  );
}

const DetailRow = ({ icon: Icon, label, val, mono }) => (
  _react2.default.createElement('div', { className: "flex items-center gap-3 p-3 rounded-2xl bg-slate-50"     ,}
    , _react2.default.createElement('div', { className: "w-9 h-9 rounded-xl bg-white flex items-center justify-center"      ,}
      , _react2.default.createElement(Icon, { className: "w-4 h-4 text-slate-600"  ,} )
    )
    , _react2.default.createElement('div', { className: "flex-1",}
      , _react2.default.createElement('p', { className: "text-xs text-slate-500" ,}, label)
      , _react2.default.createElement('p', { className: `text-sm font-semibold text-slate-900 ${mono ? 'font-mono' : ''}`,}, val)
    )
  )
);

// ============ PROFILE TAB ============
function ProfileTab() {
  const { user, setView, setUser, showToast } = useApp();

  const logout = () => {
    setUser(null);
    setView('login');
    showToast('Logged out', 'info');
  };

  const sections = [
    {
      title: 'Account',
      items: [
        { icon: _lucidereact.User, label: 'Personal Info', sub: 'Name, email, phone' },
        { icon: _lucidereact.Users, label: 'Family Members', sub: 'Manage profiles' },
        { icon: _lucidereact.Heart, label: 'Health Info', sub: 'Allergies, conditions' },
      ],
    },
    {
      title: 'Preferences',
      items: [
        { icon: _lucidereact.Bell, label: 'Notifications', sub: 'Reminders & alerts' },
        { icon: _lucidereact.Globe, label: 'Language & Region', sub: 'English (US)' },
        { icon: _lucidereact.Shield, label: 'Privacy & Security', sub: 'Manage data' },
      ],
    },
    {
      title: 'Support',
      items: [
        { icon: _lucidereact.BookOpen, label: 'Help Center', sub: 'FAQ & guides' },
        { icon: _lucidereact.Phone, label: 'Contact Us', sub: 'Get in touch' },
        { icon: _lucidereact.Star, label: 'Rate MediAlert', sub: 'Share your feedback' },
      ],
    },
  ];

  return (
    _react2.default.createElement(_framermotion.motion.div, { initial: { opacity: 0, y: 10 }, animate: { opacity: 1, y: 0 }, className: "pb-6",}
      , _react2.default.createElement('div', { className: "bg-gradient-to-br from-blue-600 to-cyan-500 px-5 pt-12 pb-20 rounded-b-3xl"      ,}
        , _react2.default.createElement('h1', { className: "text-white text-2xl font-bold mb-6"   ,}, "Profile")
        , _react2.default.createElement('div', { className: "flex items-center gap-4"  ,}
          , _react2.default.createElement('div', { className: "w-20 h-20 rounded-3xl bg-white/20 backdrop-blur border-2 border-white/40 flex items-center justify-center text-white text-2xl font-bold"            ,}
            , _optionalChain([user, 'optionalAccess', _8 => _8.avatar])
          )
          , _react2.default.createElement('div', { className: "text-white",}
            , _react2.default.createElement('p', { className: "font-bold text-xl" ,}, _optionalChain([user, 'optionalAccess', _9 => _9.name]))
            , _react2.default.createElement('p', { className: "text-cyan-100 text-sm" ,}, _optionalChain([user, 'optionalAccess', _10 => _10.email]))
            , _react2.default.createElement('div', { className: "flex items-center gap-1 mt-2 px-2.5 py-1 rounded-full bg-white/20 backdrop-blur w-fit"         ,}
              , _react2.default.createElement(_lucidereact.Award, { className: "w-3 h-3" ,} )
              , _react2.default.createElement('span', { className: "text-xs font-medium" ,}, "Premium Member" )
            )
          )
        )
      )

      , _react2.default.createElement('div', { className: "px-5 -mt-12" ,}
        , _react2.default.createElement('div', { className: "bg-white rounded-2xl p-4 shadow-lg border border-slate-100 grid grid-cols-3 gap-2 text-center mb-6"          ,}
          , [
            { v: '24', l: 'Verifications' },
            { v: '3', l: 'Medicines' },
            { v: '12', l: 'Days streak' },
          ].map((s, i) => (
            _react2.default.createElement('div', { key: i, className: i < 2 ? 'border-r border-slate-100' : '',}
              , _react2.default.createElement('p', { className: "text-2xl font-bold text-slate-900"  ,}, s.v)
              , _react2.default.createElement('p', { className: "text-xs text-slate-500" ,}, s.l)
            )
          ))
        )

        , sections.map(sec => (
          _react2.default.createElement('div', { key: sec.title, className: "mb-5",}
            , _react2.default.createElement('p', { className: "text-xs font-bold text-slate-500 uppercase tracking-wider mb-2 px-1"      ,}, sec.title)
            , _react2.default.createElement('div', { className: "bg-white rounded-2xl border border-slate-100 overflow-hidden"    ,}
              , sec.items.map((it, i) => (
                _react2.default.createElement('button', { key: i,
                  className: `w-full p-4 flex items-center gap-3 hover:bg-slate-50 transition ${
                    i < sec.items.length - 1 ? 'border-b border-slate-100' : ''
                  }`,}
                  , _react2.default.createElement('div', { className: "w-10 h-10 rounded-xl bg-slate-100 flex items-center justify-center"      ,}
                    , _react2.default.createElement(it.icon, { className: "w-5 h-5 text-slate-600"  ,} )
                  )
                  , _react2.default.createElement('div', { className: "flex-1 text-left" ,}
                    , _react2.default.createElement('p', { className: "font-semibold text-slate-900 text-sm"  ,}, it.label)
                    , _react2.default.createElement('p', { className: "text-xs text-slate-500" ,}, it.sub)
                  )
                  , _react2.default.createElement(_lucidereact.ChevronRight, { className: "w-5 h-5 text-slate-300"  ,} )
                )
              ))
            )
          )
        ))

        , _react2.default.createElement('button', { onClick: logout,
          className: "w-full p-4 rounded-2xl bg-rose-50 text-rose-600 font-semibold flex items-center justify-center gap-2"         ,}
          , _react2.default.createElement(_lucidereact.LogOut, { className: "w-5 h-5" ,} ), " Log Out"
        )

        , _react2.default.createElement('p', { className: "text-center text-xs text-slate-400 mt-4"   ,}, "MediAlert v2.0.0" )
      )
    )
  );
}

// ============ BOTTOM NAV ============
function BottomNav() {
  const { tab, setTab } = useApp();
  const tabs = [
    { k: 'home', label: 'Home', icon: _lucidereact.Home },
    { k: 'verify', label: 'Verify', icon: _lucidereact.Scan },
    { k: 'medicines', label: 'Meds', icon: _lucidereact.Pill },
    { k: 'recalls', label: 'Recalls', icon: _lucidereact.AlertOctagon },
    { k: 'profile', label: 'Profile', icon: _lucidereact.User },
  ];
  return (
    _react2.default.createElement('div', { className: "absolute bottom-0 left-0 right-0 bg-white border-t border-slate-200 px-2 pt-1.5 pb-2 z-30"          ,}
      , _react2.default.createElement('div', { className: "flex items-center justify-around"  ,}
        , tabs.map(t => {
          const active = tab === t.k;
          return (
            _react2.default.createElement('button', { key: t.k, onClick: () => setTab(t.k),
              className: "flex flex-col items-center gap-0.5 py-1.5 px-2 relative"      ,}
              , active && (
                _react2.default.createElement(_framermotion.motion.div, { layoutId: "navIndicator",
                  className: "absolute inset-0 bg-blue-50 rounded-2xl"   ,} )
              )
              , _react2.default.createElement(t.icon, { className: `relative w-5 h-5 transition ${active ? 'text-blue-600' : 'text-slate-400'}`, strokeWidth: active ? 2.5 : 2,} )
              , _react2.default.createElement('span', { className: `relative text-[10px] font-medium transition ${active ? 'text-blue-600' : 'text-slate-400'}`,}, t.label)
            )
          );
        })
      )
    )
  );
}
</script></head>
  <body>
  

<div id="preview-app"></div></body></html>

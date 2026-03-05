import { useState, useMemo } from "react";
import {
  BarChart, Bar, XAxis, YAxis, Tooltip, ResponsiveContainer,
  RadarChart, Radar, PolarGrid, PolarAngleAxis, PolarRadiusAxis,
  AreaChart, Area, CartesianGrid, PieChart, Pie, Cell, Legend
} from "recharts";

const HABIT_DATA = [
  { date: "2026-02-21", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": true, Duolingo: true, "Steps goal": false },
  { date: "2026-02-22", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": false, Duolingo: true, "Steps goal": false },
  { date: "2026-02-23", Coding: true, Journaling: false, Reading: false, "Listen to Podcast": true, Duolingo: true, "Steps goal": false },
  { date: "2026-02-26", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": false, Duolingo: false, "Steps goal": false },
  { date: "2026-02-27", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": false, Duolingo: false, "Steps goal": false },
  { date: "2026-02-28", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": false, Duolingo: false, "Steps goal": false },
  { date: "2026-03-01", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": true, Duolingo: true, "Steps goal": true },
  { date: "2026-03-02", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": true, Duolingo: true, "Steps goal": true },
  { date: "2026-03-03", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": true, Duolingo: true, "Steps goal": true },
  { date: "2026-03-04", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": true, Duolingo: true, "Steps goal": true },
  { date: "2026-03-05", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": true, Duolingo: false, "Steps goal": true },
  { date: "2026-03-06", Coding: false, Journaling: false, Reading: false, "Listen to Podcast": false, Duolingo: false, "Steps goal": false },
];

const HABITS = ["Coding", "Journaling", "Reading", "Listen to Podcast", "Duolingo", "Steps goal"];
const HABIT_ICONS = { Coding: "💻", Journaling: "📝", Reading: "📖", "Listen to Podcast": "🎧", Duolingo: "🦉", "Steps goal": "🚶" };

const COLORS = {
  bg: "#191919",
  card: "#232323",
  cardHover: "#2a2a2a",
  border: "#333",
  text: "#e8e8e8",
  textMuted: "#888",
  accent: "#4ade80",
  accentDim: "#22543d",
  warning: "#facc15",
  danger: "#f87171",
  chart: ["#4ade80", "#38bdf8", "#a78bfa", "#fb923c", "#f472b6", "#facc15"],
};

const getDayName = (dateStr) => {
  const d = new Date(dateStr + "T12:00:00");
  return d.toLocaleDateString("en-US", { weekday: "short" });
};

const getDateLabel = (dateStr) => {
  const d = new Date(dateStr + "T12:00:00");
  return d.toLocaleDateString("en-US", { month: "short", day: "numeric" });
};

const CustomTooltip = ({ active, payload, label }) => {
  if (!active || !payload?.length) return null;
  return (
    <div style={{ background: "#2a2a2a", border: "1px solid #444", borderRadius: 8, padding: "10px 14px", fontSize: 13 }}>
      <p style={{ color: "#e8e8e8", fontWeight: 600, margin: 0, marginBottom: 4 }}>{label}</p>
      {payload.map((p, i) => (
        <p key={i} style={{ color: p.color || p.fill, margin: "2px 0", fontSize: 12 }}>
          {p.name}: <strong>{typeof p.value === "number" ? (Number.isInteger(p.value) ? p.value : p.value.toFixed(1)) : p.value}</strong>
        </p>
      ))}
    </div>
  );
};

export default function HabitDashboard() {
  const [activeTab, setActiveTab] = useState("overview");

  const stats = useMemo(() => {
    const totalDays = HABIT_DATA.length;
    const habitCounts = {};
    HABITS.forEach(h => { habitCounts[h] = 0; });
    
    let perfectDays = 0;
    let totalChecks = 0;
    const dailyScores = [];
    const weeklyData = {};

    HABIT_DATA.forEach(day => {
      let done = 0;
      HABITS.forEach(h => { if (day[h]) { done++; habitCounts[h]++; } });
      totalChecks += done;
      if (done === 6) perfectDays++;
      
      const pct = Math.round((done / 6) * 100);
      dailyScores.push({
        date: getDateLabel(day.date),
        day: getDayName(day.date),
        score: pct,
        done,
        total: 6,
      });

      const weekStart = new Date(day.date + "T12:00:00");
      const dayOfWeek = weekStart.getDay();
      const mondayOffset = dayOfWeek === 0 ? -6 : 1 - dayOfWeek;
      const monday = new Date(weekStart);
      monday.setDate(weekStart.getDate() + mondayOffset);
      const weekKey = monday.toISOString().split("T")[0];
      if (!weeklyData[weekKey]) weeklyData[weekKey] = { totalDone: 0, totalPossible: 0, days: 0 };
      weeklyData[weekKey].totalDone += done;
      weeklyData[weekKey].totalPossible += 6;
      weeklyData[weekKey].days++;
    });

    const overallPct = Math.round((totalChecks / (totalDays * 6)) * 100);

    const habitRates = HABITS.map(h => ({
      habit: h,
      icon: HABIT_ICONS[h],
      rate: Math.round((habitCounts[h] / totalDays) * 100),
      count: habitCounts[h],
      total: totalDays,
    })).sort((a, b) => b.rate - a.rate);

    const radarData = HABITS.map(h => ({
      habit: h.length > 10 ? h.substring(0, 10) + "…" : h,
      fullName: h,
      rate: Math.round((habitCounts[h] / totalDays) * 100),
    }));

    // Streaks
    let currentStreak = 0;
    let bestStreak = 0;
    let tempStreak = 0;
    const sorted = [...HABIT_DATA].sort((a, b) => a.date.localeCompare(b.date));
    for (let i = 0; i < sorted.length; i++) {
      const done = HABITS.filter(h => sorted[i][h]).length;
      if (done > 0) {
        tempStreak++;
        bestStreak = Math.max(bestStreak, tempStreak);
      } else {
        tempStreak = 0;
      }
    }
    // Count back from most recent for current
    for (let i = sorted.length - 1; i >= 0; i--) {
      const done = HABITS.filter(h => sorted[i][h]).length;
      if (done > 0) currentStreak++;
      else break;
    }

    // Day of week performance
    const dayPerf = {};
    ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"].forEach(d => { dayPerf[d] = { total: 0, done: 0, count: 0 }; });
    HABIT_DATA.forEach(day => {
      const dn = getDayName(day.date);
      const done = HABITS.filter(h => day[h]).length;
      dayPerf[dn].total += 6;
      dayPerf[dn].done += done;
      dayPerf[dn].count++;
    });
    const dayOfWeekData = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"].map(d => ({
      day: d,
      avg: dayPerf[d].count > 0 ? Math.round((dayPerf[d].done / dayPerf[d].total) * 100) : 0,
    }));

    const weeklyTrend = Object.entries(weeklyData)
      .sort(([a], [b]) => a.localeCompare(b))
      .map(([week, data]) => ({
        week: getDateLabel(week),
        avg: Math.round((data.totalDone / data.totalPossible) * 100),
        days: data.days,
      }));

    return {
      totalDays, perfectDays, overallPct, totalChecks,
      habitRates, radarData, dailyScores, currentStreak, bestStreak,
      dayOfWeekData, weeklyTrend
    };
  }, []);

  const StatCard = ({ label, value, sub, color, large }) => (
    <div style={{
      background: COLORS.card,
      borderRadius: 14,
      padding: large ? "24px 20px" : "18px 16px",
      border: `1px solid ${COLORS.border}`,
      flex: 1,
      minWidth: large ? 140 : 120,
      transition: "all 0.2s",
    }}>
      <div style={{ fontSize: 11, color: COLORS.textMuted, textTransform: "uppercase", letterSpacing: "0.08em", fontWeight: 600, marginBottom: 6 }}>
        {label}
      </div>
      <div style={{ fontSize: large ? 36 : 28, fontWeight: 800, color: color || COLORS.accent, lineHeight: 1.1, fontFamily: "'JetBrains Mono', monospace" }}>
        {value}
      </div>
      {sub && <div style={{ fontSize: 11, color: COLORS.textMuted, marginTop: 4 }}>{sub}</div>}
    </div>
  );

  const tabs = [
    { id: "overview", label: "Overview" },
    { id: "habits", label: "Per Habit" },
    { id: "trends", label: "Trends" },
    { id: "streaks", label: "Streaks" },
  ];

  return (
    <div style={{
      fontFamily: "'Inter', -apple-system, sans-serif",
      background: COLORS.bg,
      color: COLORS.text,
      minHeight: "100vh",
      padding: "28px 24px",
      maxWidth: 800,
      margin: "0 auto",
    }}>
      <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;800&family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet" />

      {/* Header */}
      <div style={{ marginBottom: 28 }}>
        <div style={{ fontSize: 11, color: COLORS.textMuted, textTransform: "uppercase", letterSpacing: "0.15em", fontWeight: 600, marginBottom: 4 }}>
          Habit Analytics
        </div>
        <h1 style={{ fontSize: 28, fontWeight: 800, margin: 0, background: "linear-gradient(135deg, #4ade80, #38bdf8)", WebkitBackgroundClip: "text", WebkitTextFillColor: "transparent" }}>
          Stats Dashboard
        </h1>
        <div style={{ fontSize: 12, color: COLORS.textMuted, marginTop: 4 }}>
          Tracking {stats.totalDays} days · Feb 21 – Mar 6, 2026
        </div>
      </div>

      {/* Tabs */}
      <div style={{ display: "flex", gap: 4, marginBottom: 24, background: COLORS.card, borderRadius: 10, padding: 4, border: `1px solid ${COLORS.border}` }}>
        {tabs.map(t => (
          <button
            key={t.id}
            onClick={() => setActiveTab(t.id)}
            style={{
              flex: 1,
              padding: "10px 12px",
              border: "none",
              borderRadius: 8,
              background: activeTab === t.id ? COLORS.accent : "transparent",
              color: activeTab === t.id ? "#000" : COLORS.textMuted,
              fontWeight: activeTab === t.id ? 700 : 500,
              fontSize: 13,
              cursor: "pointer",
              transition: "all 0.2s",
              fontFamily: "inherit",
            }}
          >
            {t.label}
          </button>
        ))}
      </div>

      {/* OVERVIEW TAB */}
      {activeTab === "overview" && (
        <div>
          {/* KPI Cards */}
          <div style={{ display: "flex", gap: 12, flexWrap: "wrap", marginBottom: 24 }}>
            <StatCard label="Overall Score" value={`${stats.overallPct}%`} sub={`${stats.totalChecks} / ${stats.totalDays * 6} habits`} large />
            <StatCard label="Perfect Days" value={stats.perfectDays} sub={`out of ${stats.totalDays} days`} color={stats.perfectDays > 0 ? COLORS.warning : COLORS.danger} large />
            <StatCard label="Current Streak" value={`${stats.currentStreak}d`} sub={`Best: ${stats.bestStreak} days`} color="#38bdf8" large />
          </div>

          {/* Daily Performance Chart */}
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "20px 16px", border: `1px solid ${COLORS.border}`, marginBottom: 20 }}>
            <div style={{ fontSize: 14, fontWeight: 700, marginBottom: 16 }}>Daily Completion Rate</div>
            <ResponsiveContainer width="100%" height={220}>
              <AreaChart data={stats.dailyScores}>
                <defs>
                  <linearGradient id="scoreGrad" x1="0" y1="0" x2="0" y2="1">
                    <stop offset="0%" stopColor="#4ade80" stopOpacity={0.4} />
                    <stop offset="100%" stopColor="#4ade80" stopOpacity={0} />
                  </linearGradient>
                </defs>
                <CartesianGrid strokeDasharray="3 3" stroke="#333" />
                <XAxis dataKey="date" tick={{ fontSize: 10, fill: "#888" }} axisLine={false} tickLine={false} />
                <YAxis domain={[0, 100]} tick={{ fontSize: 10, fill: "#888" }} axisLine={false} tickLine={false} tickFormatter={v => `${v}%`} />
                <Tooltip content={<CustomTooltip />} />
                <Area type="monotone" dataKey="score" stroke="#4ade80" strokeWidth={2.5} fill="url(#scoreGrad)" name="Completion %" dot={{ r: 4, fill: "#4ade80", stroke: "#232323", strokeWidth: 2 }} />
              </AreaChart>
            </ResponsiveContainer>
          </div>

          {/* Radar */}
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "20px 16px", border: `1px solid ${COLORS.border}` }}>
            <div style={{ fontSize: 14, fontWeight: 700, marginBottom: 16 }}>Habit Radar</div>
            <ResponsiveContainer width="100%" height={260}>
              <RadarChart data={stats.radarData} outerRadius="70%">
                <PolarGrid stroke="#333" />
                <PolarAngleAxis dataKey="habit" tick={{ fontSize: 11, fill: "#ccc" }} />
                <PolarRadiusAxis domain={[0, 100]} tick={{ fontSize: 9, fill: "#666" }} axisLine={false} />
                <Radar dataKey="rate" stroke="#4ade80" fill="#4ade80" fillOpacity={0.25} strokeWidth={2} name="Rate %" />
                <Tooltip content={<CustomTooltip />} />
              </RadarChart>
            </ResponsiveContainer>
          </div>
        </div>
      )}

      {/* PER HABIT TAB */}
      {activeTab === "habits" && (
        <div>
          {/* Habit Rate Bars */}
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "20px 16px", border: `1px solid ${COLORS.border}`, marginBottom: 20 }}>
            <div style={{ fontSize: 14, fontWeight: 700, marginBottom: 18 }}>Completion Rate by Habit</div>
            {stats.habitRates.map((h, i) => (
              <div key={h.habit} style={{ marginBottom: 14 }}>
                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 6 }}>
                  <span style={{ fontSize: 13, fontWeight: 600 }}>{h.icon} {h.habit}</span>
                  <span style={{ fontSize: 13, fontWeight: 700, color: COLORS.chart[i % COLORS.chart.length], fontFamily: "'JetBrains Mono', monospace" }}>
                    {h.rate}%
                  </span>
                </div>
                <div style={{ height: 10, background: "#2a2a2a", borderRadius: 5, overflow: "hidden" }}>
                  <div style={{
                    height: "100%",
                    width: `${h.rate}%`,
                    background: `linear-gradient(90deg, ${COLORS.chart[i % COLORS.chart.length]}, ${COLORS.chart[i % COLORS.chart.length]}88)`,
                    borderRadius: 5,
                    transition: "width 0.8s ease",
                  }} />
                </div>
                <div style={{ fontSize: 10, color: COLORS.textMuted, marginTop: 3 }}>
                  {h.count} of {h.total} days
                </div>
              </div>
            ))}
          </div>

          {/* Pie Chart */}
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "20px 16px", border: `1px solid ${COLORS.border}` }}>
            <div style={{ fontSize: 14, fontWeight: 700, marginBottom: 16 }}>Share of Total Completions</div>
            <ResponsiveContainer width="100%" height={260}>
              <PieChart>
                <Pie
                  data={stats.habitRates.map(h => ({ name: h.habit, value: h.count }))}
                  cx="50%" cy="50%"
                  innerRadius={55} outerRadius={90}
                  paddingAngle={3}
                  dataKey="value"
                  stroke="none"
                >
                  {stats.habitRates.map((_, i) => (
                    <Cell key={i} fill={COLORS.chart[i % COLORS.chart.length]} />
                  ))}
                </Pie>
                <Tooltip content={<CustomTooltip />} />
                <Legend
                  iconType="circle"
                  iconSize={8}
                  wrapperStyle={{ fontSize: 11, color: "#aaa" }}
                />
              </PieChart>
            </ResponsiveContainer>
          </div>
        </div>
      )}

      {/* TRENDS TAB */}
      {activeTab === "trends" && (
        <div>
          {/* Weekly Trend */}
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "20px 16px", border: `1px solid ${COLORS.border}`, marginBottom: 20 }}>
            <div style={{ fontSize: 14, fontWeight: 700, marginBottom: 16 }}>Weekly Average Completion</div>
            <ResponsiveContainer width="100%" height={220}>
              <BarChart data={stats.weeklyTrend}>
                <CartesianGrid strokeDasharray="3 3" stroke="#333" />
                <XAxis dataKey="week" tick={{ fontSize: 11, fill: "#888" }} axisLine={false} tickLine={false} />
                <YAxis domain={[0, 100]} tick={{ fontSize: 10, fill: "#888" }} axisLine={false} tickLine={false} tickFormatter={v => `${v}%`} />
                <Tooltip content={<CustomTooltip />} />
                <Bar dataKey="avg" name="Avg %" radius={[6, 6, 0, 0]} maxBarSize={50}>
                  {stats.weeklyTrend.map((entry, i) => (
                    <Cell key={i} fill={entry.avg >= 50 ? "#4ade80" : entry.avg >= 25 ? "#facc15" : "#f87171"} />
                  ))}
                </Bar>
              </BarChart>
            </ResponsiveContainer>
          </div>

          {/* Day of Week */}
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "20px 16px", border: `1px solid ${COLORS.border}` }}>
            <div style={{ fontSize: 14, fontWeight: 700, marginBottom: 16 }}>Best Day of the Week</div>
            <ResponsiveContainer width="100%" height={220}>
              <BarChart data={stats.dayOfWeekData}>
                <CartesianGrid strokeDasharray="3 3" stroke="#333" />
                <XAxis dataKey="day" tick={{ fontSize: 11, fill: "#888" }} axisLine={false} tickLine={false} />
                <YAxis domain={[0, 100]} tick={{ fontSize: 10, fill: "#888" }} axisLine={false} tickLine={false} tickFormatter={v => `${v}%`} />
                <Tooltip content={<CustomTooltip />} />
                <Bar dataKey="avg" name="Avg Score %" radius={[6, 6, 0, 0]} maxBarSize={45}>
                  {stats.dayOfWeekData.map((entry, i) => {
                    const max = Math.max(...stats.dayOfWeekData.map(d => d.avg));
                    return <Cell key={i} fill={entry.avg === max && entry.avg > 0 ? "#4ade80" : "#38bdf8"} opacity={entry.avg === 0 ? 0.15 : 0.8} />;
                  })}
                </Bar>
              </BarChart>
            </ResponsiveContainer>
          </div>
        </div>
      )}

      {/* STREAKS TAB */}
      {activeTab === "streaks" && (
        <div>
          <div style={{ display: "flex", gap: 12, flexWrap: "wrap", marginBottom: 24 }}>
            <StatCard label="Current Streak" value={`${stats.currentStreak}`} sub="consecutive active days" color="#38bdf8" large />
            <StatCard label="Best Streak" value={`${stats.bestStreak}`} sub="all-time record" color={COLORS.warning} large />
            <StatCard label="Perfect Days" value={`${stats.perfectDays}`} sub="all 6 habits done" color={stats.perfectDays > 0 ? COLORS.accent : COLORS.danger} large />
          </div>

          {/* Activity Heatmap Grid */}
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "20px 16px", border: `1px solid ${COLORS.border}`, marginBottom: 20 }}>
            <div style={{ fontSize: 14, fontWeight: 700, marginBottom: 16 }}>Activity Heatmap</div>
            <div style={{ display: "grid", gridTemplateColumns: "repeat(7, 1fr)", gap: 6, maxWidth: 400 }}>
              {["M", "T", "W", "T", "F", "S", "S"].map((d, i) => (
                <div key={i} style={{ textAlign: "center", fontSize: 10, color: COLORS.textMuted, fontWeight: 600, paddingBottom: 4 }}>{d}</div>
              ))}
              {(() => {
                const sorted = [...HABIT_DATA].sort((a, b) => a.date.localeCompare(b.date));
                const firstDate = new Date(sorted[0].date + "T12:00:00");
                const startDayOfWeek = firstDate.getDay();
                const mondayOffset = startDayOfWeek === 0 ? 6 : startDayOfWeek - 1;
                const cells = [];
                for (let i = 0; i < mondayOffset; i++) {
                  cells.push(<div key={`empty-${i}`} style={{ aspectRatio: "1", borderRadius: 4 }} />);
                }
                
                const dateMap = {};
                HABIT_DATA.forEach(d => {
                  const done = HABITS.filter(h => d[h]).length;
                  dateMap[d.date] = done;
                });

                const startDate = new Date(firstDate);
                startDate.setDate(startDate.getDate());
                const endDate = new Date("2026-03-06T12:00:00");
                const current = new Date(startDate);
                
                while (current <= endDate) {
                  const dateStr = current.toISOString().split("T")[0];
                  const done = dateMap[dateStr];
                  const intensity = done !== undefined ? done / 6 : -1;
                  
                  let bg;
                  if (intensity < 0) bg = "#1a1a1a";
                  else if (intensity === 0) bg = "#2a1a1a";
                  else if (intensity <= 0.33) bg = "#1a3a1a";
                  else if (intensity <= 0.66) bg = "#2a5a2a";
                  else bg = "#4ade80";

                  cells.push(
                    <div
                      key={dateStr}
                      title={`${dateStr}: ${done !== undefined ? done : 0}/6`}
                      style={{
                        aspectRatio: "1",
                        borderRadius: 4,
                        background: bg,
                        border: `1px solid ${intensity >= 0 ? "#333" : "#222"}`,
                        cursor: "default",
                        transition: "transform 0.15s",
                      }}
                    />
                  );
                  current.setDate(current.getDate() + 1);
                }
                return cells;
              })()}
            </div>
            <div style={{ display: "flex", alignItems: "center", gap: 6, marginTop: 12, fontSize: 10, color: COLORS.textMuted }}>
              <span>Less</span>
              {["#2a1a1a", "#1a3a1a", "#2a5a2a", "#4ade80"].map((c, i) => (
                <div key={i} style={{ width: 14, height: 14, borderRadius: 3, background: c, border: "1px solid #333" }} />
              ))}
              <span>More</span>
            </div>
          </div>

          {/* Per-Habit Streaks */}
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "20px 16px", border: `1px solid ${COLORS.border}` }}>
            <div style={{ fontSize: 14, fontWeight: 700, marginBottom: 16 }}>Per-Habit Streaks</div>
            {HABITS.map((habit, idx) => {
              const sorted = [...HABIT_DATA].sort((a, b) => a.date.localeCompare(b.date));
              let curr = 0, best = 0, temp = 0;
              for (const day of sorted) {
                if (day[habit]) { temp++; best = Math.max(best, temp); } else { temp = 0; }
              }
              for (let i = sorted.length - 1; i >= 0; i--) {
                if (sorted[i][habit]) curr++; else break;
              }
              return (
                <div key={habit} style={{ display: "flex", alignItems: "center", justifyContent: "space-between", padding: "10px 0", borderBottom: idx < HABITS.length - 1 ? `1px solid ${COLORS.border}` : "none" }}>
                  <span style={{ fontSize: 13 }}>{HABIT_ICONS[habit]} {habit}</span>
                  <div style={{ display: "flex", gap: 16 }}>
                    <div style={{ textAlign: "right" }}>
                      <div style={{ fontSize: 16, fontWeight: 700, color: "#38bdf8", fontFamily: "'JetBrains Mono', monospace" }}>{curr}d</div>
                      <div style={{ fontSize: 9, color: COLORS.textMuted }}>CURRENT</div>
                    </div>
                    <div style={{ textAlign: "right" }}>
                      <div style={{ fontSize: 16, fontWeight: 700, color: COLORS.warning, fontFamily: "'JetBrains Mono', monospace" }}>{best}d</div>
                      <div style={{ fontSize: 9, color: COLORS.textMuted }}>BEST</div>
                    </div>
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      )}

      {/* Footer */}
      <div style={{ textAlign: "center", marginTop: 28, fontSize: 11, color: "#555" }}>
        Data synced from Notion · Clocking System
      </div>
    </div>
  );
}

import React, { useState } from 'react';

// ============================================
// DATA VERIFICADA - Fuente: Citrino Dic 2025
// ============================================

const zonasData = {
  equipetrol: {
    nombre: "Equipetrol",
    vacancia: 30,
    precio: 2036,
    alquiler: 10.7,
    capRate: 6.3,
    stock: 30,
    veredicto: "evitar",
    ocupacion: 70,
    mora: 7.0,
    descripcion: "Sobreoferta crítica (>15% vacancia). El 30% del stock de dptos en venta está aquí."
  },
  norte_2_5: {
    nombre: "Norte (2do-5to)",
    vacancia: 12,
    precio: 1657,
    alquiler: 8.5,
    capRate: 6.2,
    stock: 15,
    veredicto: "precaucion",
    ocupacion: 88,
    mora: 6.6,
    descripcion: "Zona mixta con vacancia 8-14%. Requiere análisis cuidadoso del proyecto."
  },
  norte_5_8: {
    nombre: "Norte (5to-8vo)",
    vacancia: 6,
    precio: 1454,
    alquiler: 7.1,
    capRate: 5.9,
    stock: 16,
    veredicto: "precaucion",
    ocupacion: 94,
    mora: 13.9,
    descripcion: "Buena ocupación pero mora alta (13.9%). Zona en consolidación."
  },
  sur: {
    nombre: "Zona Sur",
    vacancia: 5,
    precio: 720,
    alquiler: 5.9,
    capRate: 9.8,
    stock: 1,
    veredicto: "invertir",
    ocupacion: 95,
    mora: 13.9,
    descripcion: "Excelente ocupación. Mejor relación precio-rentabilidad de la ciudad."
  },
  este: {
    nombre: "Zona Este",
    vacancia: 4,
    precio: 552,
    alquiler: 5.2,
    capRate: 11.3,
    stock: 0.4,
    veredicto: "invertir",
    ocupacion: 96,
    mora: 12.6,
    descripcion: "El Cap Rate más alto de Santa Cruz (11.3%). Demanda real de familias."
  },
  oeste: {
    nombre: "Zona Oeste",
    vacancia: 5,
    precio: 1111,
    alquiler: 6.0,
    capRate: 6.5,
    stock: 4,
    veredicto: "invertir",
    ocupacion: 95,
    mora: 6.0,
    descripcion: "Buena ocupación y mora controlada. Equilibrio precio-estabilidad."
  },
  norte_sub: {
    nombre: "Norte Suburbano",
    vacancia: 8,
    precio: 705,
    alquiler: 6.3,
    capRate: 10.7,
    stock: 0.4,
    veredicto: "invertir",
    ocupacion: 92,
    mora: 7.9,
    descripcion: "Alto Cap Rate (10.7%) con precio accesible. Segunda mejor rentabilidad."
  }
};

const tipologiaData = {
  monoambiente: { nombre: "Monoambiente", perfil: "Inversores yield" },
  "1d": { nombre: "1 Dormitorio", perfil: "Parejas jóvenes" },
  "2d": { nombre: "2 Dormitorios", perfil: "Familias pequeñas" },
  "3d": { nombre: "3+ Dormitorios", perfil: "Familias consolidadas" }
};

const matrizInversion = {
  equipetrol: { monoambiente: "evitar", "1d": "evitar", "2d": "evitar", "3d": "evitar" },
  norte_2_5: { monoambiente: "precaucion", "1d": "precaucion", "2d": "precaucion", "3d": "precaucion" },
  norte_5_8: { monoambiente: "precaucion", "1d": "precaucion", "2d": "precaucion", "3d": "precaucion" },
  sur: { monoambiente: "invertir", "1d": "invertir", "2d": "invertir", "3d": "precaucion" },
  este: { monoambiente: "invertir", "1d": "invertir", "2d": "invertir", "3d": "precaucion" },
  oeste: { monoambiente: "invertir", "1d": "invertir", "2d": "precaucion", "3d": "precaucion" },
  norte_sub: { monoambiente: "invertir", "1d": "invertir", "2d": "invertir", "3d": "precaucion" }
};

// ============================================
// COMPONENTE PRINCIPAL
// ============================================
export default function App() {
  const [tab, setTab] = useState('inicio');
  const [zonaSeleccionada, setZonaSeleccionada] = useState('este');
  const [tipoSeleccionado, setTipoSeleccionado] = useState('2d');
  const [zonaCompare1, setZonaCompare1] = useState('equipetrol');
  const [zonaCompare2, setZonaCompare2] = useState('este');
  const [metrosCuadrados, setMetrosCuadrados] = useState(60);

  const tabs = [
    { id: 'inicio', label: 'Inicio' },
    { id: 'macro', label: 'Macro' },
    { id: 'mapa', label: 'Mapa' },
    { id: 'simulador', label: 'Simular' },
    { id: 'comparar', label: 'VS' },
    { id: 'mora', label: 'Mora' },
    { id: 'predicciones', label: '2026' }
  ];

  // Calcular ROI
  const calcularROI = (zona) => {
    const data = zonasData[zona];
    return ((data.alquiler * 12) / data.precio * 100).toFixed(1);
  };

  // Calcular Payback
  const calcularPayback = (zona) => {
    const data = zonasData[zona];
    return (data.precio / (data.alquiler * 12)).toFixed(1);
  };

  return (
    <div style={{
      minHeight: '100vh',
      background: 'linear-gradient(180deg, #0a0f1a 0%, #131c2e 50%, #0a0f1a 100%)',
      color: 'white',
      fontFamily: 'system-ui, -apple-system, sans-serif'
    }}>
      
      {/* Header */}
      <header style={{
        display: 'flex',
        justifyContent: 'space-between',
        alignItems: 'center',
        padding: '16px 20px',
        borderBottom: '1px solid rgba(255,255,255,0.08)'
      }}>
        <div style={{ display: 'flex', alignItems: 'center', gap: '12px' }}>
          <div style={{
            width: '40px',
            height: '40px',
            background: 'linear-gradient(135deg, #1e3a5f 0%, #0f2744 100%)',
            borderRadius: '10px',
            display: 'flex',
            alignItems: 'center',
            justifyContent: 'center',
            fontSize: '22px',
            fontWeight: '700',
            color: '#c9a227'
          }}>S</div>
          <div>
            <h1 style={{ margin: 0, fontSize: '18px', fontWeight: '700' }}>Simón | Inteligencia Inmobiliaria</h1>
            <p style={{ margin: 0, fontSize: '12px', color: '#64748b' }}>Tu copiloto inmobiliario en Santa Cruz</p>
          </div>
        </div>
        <button 
          onClick={() => window.open('/simon-inteligencia-inmobiliaria-dic2025.pdf', '_blank')}
          style={{
            background: 'linear-gradient(135deg, #ef4444 0%, #dc2626 100%)',
            border: 'none',
            borderRadius: '8px',
            padding: '10px 16px',
            color: 'white',
            fontWeight: '600',
            fontSize: '13px',
            cursor: 'pointer',
            display: 'flex',
            alignItems: 'center',
            gap: '6px'
          }}
        >
          📄 PDF Gratis
        </button>
      </header>

      {/* Tabs */}
      <nav style={{
        display: 'flex',
        justifyContent: 'center',
        gap: '4px',
        padding: '12px 16px',
        borderBottom: '1px solid rgba(255,255,255,0.08)',
        overflowX: 'auto'
      }}>
        {tabs.map(t => (
          <button
            key={t.id}
            onClick={() => setTab(t.id)}
            style={{
              padding: '10px 16px',
              borderRadius: '10px',
              border: 'none',
              background: tab === t.id 
                ? 'linear-gradient(135deg, #1e3a5f 0%, #0f2744 100%)' 
                : 'rgba(255,255,255,0.05)',
              color: tab === t.id ? 'white' : '#94a3b8',
              cursor: 'pointer',
              fontSize: '13px',
              fontWeight: tab === t.id ? '600' : '400',
              transition: 'all 0.2s',
              whiteSpace: 'nowrap'
            }}
          >
            <span>{t.label}</span>
          </button>
        ))}
      </nav>

      {/* Content */}
      <main style={{ padding: '24px 20px', maxWidth: '640px', margin: '0 auto' }}>
        
        {/* ==================== TAB: INICIO ==================== */}
        {tab === 'inicio' && (
          <div>
            {/* Badge */}
            <div style={{ textAlign: 'center', marginBottom: '16px' }}>
              <span style={{
                background: 'rgba(59, 130, 246, 0.15)',
                border: '1px solid rgba(59, 130, 246, 0.3)',
                borderRadius: '100px',
                padding: '8px 16px',
                fontSize: '13px',
                color: '#60a5fa'
              }}>
                🚀 Primer análisis independiente de Bolivia
              </span>
            </div>

            {/* Hero */}
            <h2 style={{ 
              textAlign: 'center', 
              fontSize: '32px', 
              fontWeight: '700',
              margin: '0 0 8px 0',
              lineHeight: '1.2'
            }}>
              El mercado inmobiliario<br/>
              <span style={{ color: '#22c55e' }}>como nunca lo viste</span>
            </h2>
            <p style={{ 
              textAlign: 'center', 
              color: '#64748b', 
              marginBottom: '24px',
              fontSize: '15px'
            }}>
              Data real, análisis profundo, recomendaciones accionables.
            </p>

            {/* CTAs */}
            <div style={{ display: 'flex', gap: '12px', justifyContent: 'center', marginBottom: '32px' }}>
              <button
                onClick={() => setTab('simulador')}
                style={{
                  background: 'linear-gradient(135deg, #1e3a5f 0%, #0f2744 100%)',
                  border: 'none',
                  borderRadius: '10px',
                  padding: '14px 24px',
                  color: 'white',
                  fontWeight: '600',
                  fontSize: '14px',
                  cursor: 'pointer',
                  display: 'flex',
                  alignItems: 'center',
                  gap: '8px'
                }}
              >
                Analizar mi inversión
              </button>
              <button
                onClick={() => setTab('mapa')}
                style={{
                  background: 'rgba(255,255,255,0.08)',
                  border: '1px solid rgba(255,255,255,0.15)',
                  borderRadius: '10px',
                  padding: '14px 24px',
                  color: 'white',
                  fontWeight: '600',
                  fontSize: '14px',
                  cursor: 'pointer',
                  display: 'flex',
                  alignItems: 'center',
                  gap: '8px'
                }}
              >
                Ver mapa
              </button>
            </div>

            {/* KPIs Grid */}
            <div style={{ 
              display: 'grid', 
              gridTemplateColumns: 'repeat(2, 1fr)', 
              gap: '12px',
              marginBottom: '24px'
            }}>
              <div style={{
                background: 'rgba(255,255,255,0.03)',
                borderRadius: '12px',
                padding: '20px',
                border: '1px solid rgba(255,255,255,0.06)'
              }}>
                <p style={{ color: '#64748b', fontSize: '13px', margin: '0 0 8px 0' }}>Inflación</p>
                <p style={{ color: '#ef4444', fontSize: '28px', fontWeight: '700', margin: 0 }}>19.69%</p>
              </div>
              <div style={{
                background: 'rgba(255,255,255,0.03)',
                borderRadius: '12px',
                padding: '20px',
                border: '1px solid rgba(255,255,255,0.06)'
              }}>
                <p style={{ color: '#64748b', fontSize: '13px', margin: '0 0 8px 0' }}>Mora Hipotecaria</p>
                <p style={{ color: '#3b82f6', fontSize: '28px', fontWeight: '700', margin: 0 }}>3.9%</p>
              </div>
              <div style={{
                background: 'rgba(255,255,255,0.03)',
                borderRadius: '12px',
                padding: '20px',
                border: '1px solid rgba(255,255,255,0.06)'
              }}>
                <p style={{ color: '#64748b', fontSize: '13px', margin: '0 0 8px 0' }}>Mejor Cap Rate</p>
                <p style={{ color: '#10b981', fontSize: '28px', fontWeight: '700', margin: 0 }}>11.3%</p>
              </div>
              <div style={{
                background: 'rgba(255,255,255,0.03)',
                borderRadius: '12px',
                padding: '20px',
                border: '1px solid rgba(255,255,255,0.06)'
              }}>
                <p style={{ color: '#64748b', fontSize: '13px', margin: '0 0 8px 0' }}>Vacancia Equipetrol</p>
                <p style={{ color: '#ef4444', fontSize: '28px', fontWeight: '700', margin: 0 }}>30%</p>
              </div>
            </div>

            {/* Insight Box */}
            <div style={{
              background: 'linear-gradient(135deg, rgba(34, 197, 94, 0.1) 0%, rgba(34, 197, 94, 0.05) 100%)',
              borderRadius: '12px',
              padding: '20px',
              border: '1px solid rgba(34, 197, 94, 0.2)'
            }}>
              <h3 style={{ color: '#22c55e', margin: '0 0 12px 0', fontSize: '16px' }}>
                💡 Dato clave: Quien compró en Feb 2025 duplicó
              </h3>
              <p style={{ color: '#94a3b8', fontSize: '14px', margin: 0, lineHeight: '1.6' }}>
                Precio real tocó piso en <strong style={{ color: 'white' }}>$645/m²</strong> (Feb 2025). 
                Hoy está en <strong style={{ color: 'white' }}>$1,329/m²</strong>. 
                Recuperación del <strong style={{ color: '#22c55e' }}>+106%</strong> en 10 meses.
              </p>
            </div>

            {/* Top Zonas */}
            <div style={{
              marginTop: '20px',
              background: 'rgba(255,255,255,0.03)',
              borderRadius: '12px',
              padding: '20px',
              border: '1px solid rgba(255,255,255,0.06)'
            }}>
              <h3 style={{ margin: '0 0 16px 0', fontSize: '16px' }}>🏆 Top Zonas por Rentabilidad</h3>
              {[
                { zona: 'este', medal: '🥇' },
                { zona: 'norte_sub', medal: '🥈' },
                { zona: 'sur', medal: '🥉' }
              ].map(({ zona, medal }) => (
                <div key={zona} style={{
                  display: 'flex',
                  justifyContent: 'space-between',
                  alignItems: 'center',
                  padding: '12px 0',
                  borderBottom: '1px solid rgba(255,255,255,0.06)'
                }}>
                  <span style={{ fontSize: '14px' }}>{medal} {zonasData[zona].nombre}</span>
                  <div style={{ textAlign: 'right' }}>
                    <span style={{ color: '#22c55e', fontWeight: '700' }}>{zonasData[zona].capRate}% Cap</span>
                    <span style={{ color: '#64748b', marginLeft: '12px', fontSize: '13px' }}>${zonasData[zona].precio}/m²</span>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* ==================== TAB: MACRO ==================== */}
        {tab === 'macro' && (
          <div>
            <h2 style={{ textAlign: 'center', fontSize: '24px', margin: '0 0 8px 0' }}>📊 Contexto Macro</h2>
            <p style={{ textAlign: 'center', color: '#64748b', marginBottom: '24px' }}>Bolivia y el mercado inmobiliario</p>

            <div style={{ display: 'flex', flexDirection: 'column', gap: '16px' }}>
              {/* Alerta */}
              <div style={{
                background: 'rgba(239, 68, 68, 0.08)',
                borderRadius: '12px',
                padding: '20px',
                border: '1px solid rgba(239, 68, 68, 0.2)'
              }}>
                <h3 style={{ color: '#f87171', margin: '0 0 12px 0', fontSize: '16px' }}>⚠️ Señales de Alerta</h3>
                <ul style={{ margin: 0, paddingLeft: '20px', color: '#cbd5e1', fontSize: '14px', lineHeight: '1.8' }}>
                  <li>Inflación acumulada ~20% (no transables)</li>
                  <li>Tipo de cambio paralelo ~Bs 10.36</li>
                  <li>Déficit fiscal sostenido desde 2012</li>
                  <li>Mora hipotecaria en ascenso: 3.9%</li>
                </ul>
              </div>

              {/* Oportunidad */}
              <div style={{
                background: 'rgba(34, 197, 94, 0.08)',
                borderRadius: '12px',
                padding: '20px',
                border: '1px solid rgba(34, 197, 94, 0.2)'
              }}>
                <h3 style={{ color: '#4ade80', margin: '0 0 12px 0', fontSize: '16px' }}>✅ Oportunidades</h3>
                <ul style={{ margin: 0, paddingLeft: '20px', color: '#cbd5e1', fontSize: '14px', lineHeight: '1.8' }}>
                  <li>Precio real recuperó: $1,329/m² (+106% vs piso)</li>
                  <li>Stock en venta cayó 40% (2,791 unidades)</li>
                  <li>Cap Rate general: 6.2% (zonas periféricas &gt;10%)</li>
                  <li>Ladrillo como resguardo de valor</li>
                </ul>
              </div>

              {/* Ciclo */}
              <div style={{
                background: 'rgba(59, 130, 246, 0.08)',
                borderRadius: '12px',
                padding: '20px',
                border: '1px solid rgba(59, 130, 246, 0.2)'
              }}>
                <h3 style={{ color: '#60a5fa', margin: '0 0 12px 0', fontSize: '16px' }}>📈 Ciclo Actual: Recuperación</h3>
                <p style={{ color: '#cbd5e1', fontSize: '14px', margin: 0, lineHeight: '1.6' }}>
                  Ocupación tocó piso (93.7%) y muestra leve mejora. Proyectos de casas cayeron 77%. 
                  La absorción del stock tardará <strong style={{ color: 'white' }}>3-5 años</strong>.
                </p>
              </div>

              {/* Gráfico Evolución Precios */}
              <div style={{
                background: 'rgba(255,255,255,0.03)',
                borderRadius: '12px',
                padding: '20px',
                border: '1px solid rgba(255,255,255,0.06)'
              }}>
                <h3 style={{ margin: '0 0 20px 0', fontSize: '16px' }}>📊 Evolución Precio Real $/m²</h3>
                
                <div style={{ display: 'flex', alignItems: 'flex-end', gap: '8px', height: '180px', marginBottom: '12px' }}>
                  {[
                    { mes: 'Ago 22', valor: 1176, color: '#64748b' },
                    { mes: 'Feb 23', valor: 980, color: '#64748b' },
                    { mes: 'Ago 23', valor: 850, color: '#64748b' },
                    { mes: 'Feb 24', valor: 720, color: '#f59e0b' },
                    { mes: 'Ago 24', valor: 680, color: '#f59e0b' },
                    { mes: 'Feb 25', valor: 645, color: '#ef4444' },
                    { mes: 'Jun 25', valor: 890, color: '#22c55e' },
                    { mes: 'Dic 25', valor: 1329, color: '#22c55e' }
                  ].map((item, i) => {
                    const maxVal = 1400;
                    const height = (item.valor / maxVal) * 150;
                    
                    return (
                      <div key={i} style={{ flex: 1, display: 'flex', flexDirection: 'column', alignItems: 'center' }}>
                        <span style={{ fontSize: '10px', color: item.color, fontWeight: '600', marginBottom: '4px' }}>
                          ${item.valor}
                        </span>
                        <div style={{
                          width: '100%',
                          height: `${height}px`,
                          backgroundColor: item.color,
                          borderRadius: '4px 4px 0 0',
                          transition: 'height 0.5s ease'
                        }}></div>
                        <span style={{ fontSize: '9px', color: '#64748b', marginTop: '6px', textAlign: 'center' }}>
                          {item.mes}
                        </span>
                      </div>
                    );
                  })}
                </div>

                <div style={{
                  display: 'flex',
                  justifyContent: 'space-between',
                  padding: '12px',
                  background: 'rgba(34, 197, 94, 0.1)',
                  borderRadius: '8px',
                  border: '1px solid rgba(34, 197, 94, 0.2)'
                }}>
                  <div>
                    <p style={{ color: '#64748b', fontSize: '11px', margin: 0 }}>Piso (Feb 25)</p>
                    <p style={{ color: '#ef4444', fontSize: '18px', fontWeight: '700', margin: 0 }}>$645</p>
                  </div>
                  <div style={{ textAlign: 'center' }}>
                    <p style={{ color: '#64748b', fontSize: '11px', margin: 0 }}>Recuperación</p>
                    <p style={{ color: '#22c55e', fontSize: '18px', fontWeight: '700', margin: 0 }}>+106%</p>
                  </div>
                  <div style={{ textAlign: 'right' }}>
                    <p style={{ color: '#64748b', fontSize: '11px', margin: 0 }}>Actual (Dic 25)</p>
                    <p style={{ color: '#22c55e', fontSize: '18px', fontWeight: '700', margin: 0 }}>$1,329</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        )}

        {/* ==================== TAB: MAPA ==================== */}
        {tab === 'mapa' && (
          <div>
            <h2 style={{ textAlign: 'center', fontSize: '24px', margin: '0 0 8px 0' }}>🗺️ Mapa de Zonas</h2>
            <p style={{ textAlign: 'center', color: '#64748b', marginBottom: '24px' }}>Seleccioná una zona para ver detalles</p>

            {/* Selector de zonas */}
            <div style={{ 
              display: 'grid', 
              gridTemplateColumns: 'repeat(2, 1fr)', 
              gap: '8px',
              marginBottom: '20px'
            }}>
              {Object.entries(zonasData).map(([key, data]) => {
                const isSelected = zonaSeleccionada === key;
                const colorBg = data.veredicto === 'invertir' ? '#10b981' 
                  : data.veredicto === 'precaucion' ? '#f59e0b' : '#ef4444';
                
                return (
                  <button
                    key={key}
                    onClick={() => setZonaSeleccionada(key)}
                    style={{
                      padding: '14px',
                      borderRadius: '10px',
                      border: isSelected ? `2px solid ${colorBg}` : '1px solid rgba(255,255,255,0.1)',
                      background: isSelected ? `${colorBg}15` : 'rgba(255,255,255,0.03)',
                      color: 'white',
                      cursor: 'pointer',
                      textAlign: 'left'
                    }}
                  >
                    <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
                      <span style={{ fontWeight: '600', fontSize: '14px' }}>{data.nombre}</span>
                      <span style={{ 
                        fontSize: '11px', 
                        padding: '4px 8px', 
                        borderRadius: '100px',
                        backgroundColor: colorBg,
                        color: 'white'
                      }}>
                        {data.capRate}%
                      </span>
                    </div>
                  </button>
                );
              })}
            </div>

            {/* Detalle de zona */}
            {zonaSeleccionada && (
              <div style={{
                background: 'rgba(255,255,255,0.03)',
                borderRadius: '16px',
                padding: '24px',
                border: '1px solid rgba(255,255,255,0.08)'
              }}>
                <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'flex-start', marginBottom: '20px' }}>
                  <div>
                    <h3 style={{ margin: 0, fontSize: '22px' }}>{zonasData[zonaSeleccionada].nombre}</h3>
                    <span style={{
                      display: 'inline-block',
                      marginTop: '8px',
                      padding: '6px 12px',
                      borderRadius: '100px',
                      fontSize: '12px',
                      fontWeight: '600',
                      backgroundColor: zonasData[zonaSeleccionada].veredicto === 'invertir' ? '#10b981' 
                        : zonasData[zonaSeleccionada].veredicto === 'precaucion' ? '#f59e0b' : '#ef4444'
                    }}>
                      {zonasData[zonaSeleccionada].veredicto === 'invertir' && '✅ INVERTIR'}
                      {zonasData[zonaSeleccionada].veredicto === 'precaucion' && '⚠️ PRECAUCIÓN'}
                      {zonasData[zonaSeleccionada].veredicto === 'evitar' && '❌ EVITAR'}
                    </span>
                  </div>
                </div>

                {/* Métricas principales */}
                <div style={{ display: 'grid', gridTemplateColumns: 'repeat(3, 1fr)', gap: '16px', marginBottom: '20px' }}>
                  <div style={{ textAlign: 'center' }}>
                    <p style={{ color: '#64748b', fontSize: '12px', margin: '0 0 4px 0' }}>Precio/m²</p>
                    <p style={{ color: '#c084fc', fontSize: '22px', fontWeight: '700', margin: 0 }}>${zonasData[zonaSeleccionada].precio}</p>
                  </div>
                  <div style={{ textAlign: 'center' }}>
                    <p style={{ color: '#64748b', fontSize: '12px', margin: '0 0 4px 0' }}>Cap Rate</p>
                    <p style={{ color: '#22c55e', fontSize: '22px', fontWeight: '700', margin: 0 }}>{zonasData[zonaSeleccionada].capRate}%</p>
                  </div>
                  <div style={{ textAlign: 'center' }}>
                    <p style={{ color: '#64748b', fontSize: '12px', margin: '0 0 4px 0' }}>Vacancia</p>
                    <p style={{ color: '#60a5fa', fontSize: '22px', fontWeight: '700', margin: 0 }}>{zonasData[zonaSeleccionada].vacancia}%</p>
                  </div>
                </div>

                {/* Métricas secundarias */}
                <div style={{ display: 'grid', gridTemplateColumns: 'repeat(3, 1fr)', gap: '16px', marginBottom: '20px' }}>
                  <div style={{ textAlign: 'center' }}>
                    <p style={{ color: '#64748b', fontSize: '12px', margin: '0 0 4px 0' }}>Alquiler/m²</p>
                    <p style={{ color: '#fbbf24', fontSize: '18px', fontWeight: '600', margin: 0 }}>${zonasData[zonaSeleccionada].alquiler}</p>
                  </div>
                  <div style={{ textAlign: 'center' }}>
                    <p style={{ color: '#64748b', fontSize: '12px', margin: '0 0 4px 0' }}>Mora zona</p>
                    <p style={{ color: '#f87171', fontSize: '18px', fontWeight: '600', margin: 0 }}>{zonasData[zonaSeleccionada].mora}%</p>
                  </div>
                  <div style={{ textAlign: 'center' }}>
                    <p style={{ color: '#64748b', fontSize: '12px', margin: '0 0 4px 0' }}>Stock venta</p>
                    <p style={{ color: '#94a3b8', fontSize: '18px', fontWeight: '600', margin: 0 }}>{zonasData[zonaSeleccionada].stock}%</p>
                  </div>
                </div>

                {/* ROI Calculator con input m² */}
                <div style={{
                  background: 'rgba(34, 197, 94, 0.1)',
                  borderRadius: '10px',
                  padding: '16px',
                  border: '1px solid rgba(34, 197, 94, 0.2)',
                  marginBottom: '16px'
                }}>
                  <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: '12px' }}>
                    <p style={{ color: '#4ade80', fontSize: '13px', fontWeight: '600', margin: 0 }}>💰 Simulación ROI</p>
                    <div style={{ display: 'flex', alignItems: 'center', gap: '8px' }}>
                      <input
                        type="number"
                        value={metrosCuadrados}
                        onChange={(e) => setMetrosCuadrados(Math.max(1, parseInt(e.target.value) || 60))}
                        style={{
                          width: '60px',
                          padding: '6px 8px',
                          borderRadius: '6px',
                          border: '1px solid rgba(34, 197, 94, 0.3)',
                          background: 'rgba(0,0,0,0.3)',
                          color: 'white',
                          fontSize: '14px',
                          textAlign: 'center'
                        }}
                      />
                      <span style={{ color: '#64748b', fontSize: '13px' }}>m²</span>
                    </div>
                  </div>
                  <div style={{ display: 'grid', gridTemplateColumns: 'repeat(3, 1fr)', gap: '12px' }}>
                    <div>
                      <p style={{ color: '#64748b', fontSize: '11px', margin: 0 }}>Inversión</p>
                      <p style={{ color: 'white', fontSize: '14px', fontWeight: '600', margin: 0 }}>${(zonasData[zonaSeleccionada].precio * metrosCuadrados).toLocaleString()}</p>
                    </div>
                    <div>
                      <p style={{ color: '#64748b', fontSize: '11px', margin: 0 }}>Alquiler/mes</p>
                      <p style={{ color: 'white', fontSize: '14px', fontWeight: '600', margin: 0 }}>${(zonasData[zonaSeleccionada].alquiler * metrosCuadrados).toFixed(0)}</p>
                    </div>
                    <div>
                      <p style={{ color: '#64748b', fontSize: '11px', margin: 0 }}>Payback</p>
                      <p style={{ color: '#4ade80', fontSize: '14px', fontWeight: '600', margin: 0 }}>{calcularPayback(zonaSeleccionada)} años</p>
                    </div>
                  </div>
                </div>

                <p style={{ color: '#94a3b8', fontSize: '14px', margin: 0, lineHeight: '1.6' }}>
                  {zonasData[zonaSeleccionada].descripcion}
                </p>
              </div>
            )}
          </div>
        )}

        {/* ==================== TAB: SIMULADOR ==================== */}
        {tab === 'simulador' && (
          <div>
            <h2 style={{ textAlign: 'center', fontSize: '24px', margin: '0 0 8px 0' }}>🎯 Simulador</h2>
            <p style={{ textAlign: 'center', color: '#64748b', marginBottom: '24px' }}>¿Dónde y qué comprar?</p>

            {/* Selector Zona */}
            <div style={{
              background: 'rgba(255,255,255,0.03)',
              borderRadius: '12px',
              padding: '20px',
              marginBottom: '16px',
              border: '1px solid rgba(255,255,255,0.06)'
            }}>
              <p style={{ color: '#64748b', fontSize: '13px', margin: '0 0 12px 0' }}>📍 Zona</p>
              <div style={{ display: 'grid', gridTemplateColumns: 'repeat(2, 1fr)', gap: '8px' }}>
                {Object.entries(zonasData).map(([key, data]) => (
                  <button
                    key={key}
                    onClick={() => setZonaSeleccionada(key)}
                    style={{
                      padding: '12px',
                      borderRadius: '8px',
                      border: 'none',
                      cursor: 'pointer',
                      textAlign: 'left',
                      background: zonaSeleccionada === key 
                        ? 'linear-gradient(135deg, #1e3a5f 0%, #0f2744 100%)' 
                        : 'rgba(255,255,255,0.05)',
                      color: 'white'
                    }}
                  >
                    <p style={{ margin: 0, fontWeight: '600', fontSize: '13px' }}>{data.nombre}</p>
                    <p style={{ margin: '4px 0 0 0', fontSize: '11px', opacity: 0.7 }}>{data.capRate}% Cap • ${data.precio}/m²</p>
                  </button>
                ))}
              </div>
            </div>

            {/* Selector Tipología */}
            <div style={{
              background: 'rgba(255,255,255,0.03)',
              borderRadius: '12px',
              padding: '20px',
              marginBottom: '20px',
              border: '1px solid rgba(255,255,255,0.06)'
            }}>
              <p style={{ color: '#64748b', fontSize: '13px', margin: '0 0 12px 0' }}>🏠 Tipología</p>
              <div style={{ display: 'grid', gridTemplateColumns: 'repeat(2, 1fr)', gap: '8px' }}>
                {Object.entries(tipologiaData).map(([key, data]) => (
                  <button
                    key={key}
                    onClick={() => setTipoSeleccionado(key)}
                    style={{
                      padding: '12px',
                      borderRadius: '8px',
                      border: 'none',
                      cursor: 'pointer',
                      textAlign: 'left',
                      background: tipoSeleccionado === key 
                        ? 'linear-gradient(135deg, #8b5cf6 0%, #7c3aed 100%)' 
                        : 'rgba(255,255,255,0.05)',
                      color: 'white'
                    }}
                  >
                    <p style={{ margin: 0, fontWeight: '600', fontSize: '14px' }}>{data.nombre}</p>
                    <p style={{ margin: '4px 0 0 0', fontSize: '11px', opacity: 0.7 }}>{data.perfil}</p>
                  </button>
                ))}
              </div>
            </div>

            {/* Resultado */}
            {(() => {
              const resultado = matrizInversion[zonaSeleccionada]?.[tipoSeleccionado] || 'precaucion';
              const zona = zonasData[zonaSeleccionada];
              const colors = resultado === 'invertir' 
                ? { bg: 'rgba(16, 185, 129, 0.15)', border: '#10b981', text: '#34d399' }
                : resultado === 'precaucion'
                ? { bg: 'rgba(245, 158, 11, 0.15)', border: '#f59e0b', text: '#fbbf24' }
                : { bg: 'rgba(239, 68, 68, 0.15)', border: '#ef4444', text: '#f87171' };

              return (
                <div style={{
                  background: colors.bg,
                  borderRadius: '16px',
                  padding: '24px',
                  border: `2px solid ${colors.border}`
                }}>
                  <div style={{ textAlign: 'center', marginBottom: '20px' }}>
                    <span style={{ fontSize: '48px' }}>
                      {resultado === 'invertir' ? '✅' : resultado === 'precaucion' ? '⚠️' : '❌'}
                    </span>
                    <h3 style={{ color: colors.text, margin: '12px 0 4px 0', fontSize: '20px' }}>
                      {resultado === 'invertir' ? 'RECOMENDADO' : resultado === 'precaucion' ? 'ANALIZAR CASO' : 'NO RECOMENDADO'}
                    </h3>
                    <p style={{ color: '#94a3b8', margin: 0, fontSize: '14px' }}>
                      {zona.nombre} • {tipologiaData[tipoSeleccionado].nombre}
                    </p>
                  </div>

                  <div style={{ display: 'grid', gridTemplateColumns: 'repeat(2, 1fr)', gap: '12px', marginBottom: '20px' }}>
                    <div style={{ background: 'rgba(0,0,0,0.2)', borderRadius: '10px', padding: '14px', textAlign: 'center' }}>
                      <p style={{ color: '#64748b', fontSize: '12px', margin: 0 }}>Cap Rate</p>
                      <p style={{ color: colors.text, fontSize: '24px', fontWeight: '700', margin: '4px 0 0 0' }}>{zona.capRate}%</p>
                    </div>
                    <div style={{ background: 'rgba(0,0,0,0.2)', borderRadius: '10px', padding: '14px', textAlign: 'center' }}>
                      <p style={{ color: '#64748b', fontSize: '12px', margin: 0 }}>Payback</p>
                      <p style={{ color: colors.text, fontSize: '24px', fontWeight: '700', margin: '4px 0 0 0' }}>{calcularPayback(zonaSeleccionada)}a</p>
                    </div>
                  </div>

                  <button
                    onClick={() => {
                      const texto = `🏠 Mi análisis SCZ:\n\n📍 ${zona.nombre} + ${tipologiaData[tipoSeleccionado].nombre}\n${resultado === 'invertir' ? '✅' : resultado === 'precaucion' ? '⚠️' : '❌'} ${resultado === 'invertir' ? 'RECOMENDADO' : resultado === 'precaucion' ? 'ANALIZAR' : 'NO RECOMENDADO'}\n\n💰 Cap Rate: ${zona.capRate}%\n🏢 Vacancia: ${zona.vacancia}%\n💵 Precio: $${zona.precio}/m²\n⏱️ Payback: ${calcularPayback(zonaSeleccionada)} años\n\n📊 Fuente: Citrino Dic 2025`;
                      if (navigator.share) {
                        navigator.share({ text: texto });
                      } else {
                        navigator.clipboard.writeText(texto);
                        alert('¡Copiado! Pegalo en WhatsApp.');
                      }
                    }}
                    style={{
                      width: '100%',
                      padding: '14px',
                      backgroundColor: 'white',
                      color: '#0f172a',
                      border: 'none',
                      borderRadius: '10px',
                      fontWeight: '600',
                      fontSize: '14px',
                      cursor: 'pointer'
                    }}
                  >
                    📤 Compartir en WhatsApp
                  </button>
                </div>
              );
            })()}

            {/* Matriz */}
            <div style={{
              marginTop: '20px',
              background: 'rgba(255,255,255,0.03)',
              borderRadius: '12px',
              padding: '20px',
              border: '1px solid rgba(255,255,255,0.06)',
              overflowX: 'auto'
            }}>
              <h3 style={{ margin: '0 0 16px 0', fontSize: '16px' }}>📊 Matriz Completa</h3>
              <table style={{ width: '100%', borderCollapse: 'collapse', fontSize: '12px' }}>
                <thead>
                  <tr>
                    <th style={{ textAlign: 'left', padding: '10px 6px', color: '#64748b', borderBottom: '1px solid rgba(255,255,255,0.1)' }}>Zona</th>
                    <th style={{ textAlign: 'center', padding: '10px 6px', color: '#64748b', borderBottom: '1px solid rgba(255,255,255,0.1)' }}>Mono</th>
                    <th style={{ textAlign: 'center', padding: '10px 6px', color: '#64748b', borderBottom: '1px solid rgba(255,255,255,0.1)' }}>1D</th>
                    <th style={{ textAlign: 'center', padding: '10px 6px', color: '#64748b', borderBottom: '1px solid rgba(255,255,255,0.1)' }}>2D</th>
                    <th style={{ textAlign: 'center', padding: '10px 6px', color: '#64748b', borderBottom: '1px solid rgba(255,255,255,0.1)' }}>3D+</th>
                  </tr>
                </thead>
                <tbody>
                  {Object.entries(matrizInversion).map(([zona, tipos]) => (
                    <tr key={zona}>
                      <td style={{ padding: '10px 6px', fontWeight: '500', fontSize: '12px' }}>{zonasData[zona].nombre}</td>
                      {Object.values(tipos).map((v, i) => (
                        <td key={i} style={{ textAlign: 'center', padding: '10px 6px', fontSize: '16px' }}>
                          {v === 'invertir' ? '🟢' : v === 'precaucion' ? '🟡' : '🔴'}
                        </td>
                      ))}
                    </tr>
                  ))}
                </tbody>
              </table>
            </div>
          </div>
        )}

        {/* ==================== TAB: COMPARAR ==================== */}
        {tab === 'comparar' && (
          <div>
            <h2 style={{ textAlign: 'center', fontSize: '24px', margin: '0 0 8px 0' }}>⚔️ Comparador</h2>
            <p style={{ textAlign: 'center', color: '#64748b', marginBottom: '24px' }}>Enfrentá dos zonas</p>

            {/* Selectores */}
            <div style={{ display: 'grid', gridTemplateColumns: '1fr auto 1fr', gap: '12px', marginBottom: '24px', alignItems: 'center' }}>
              <select
                value={zonaCompare1}
                onChange={(e) => setZonaCompare1(e.target.value)}
                style={{
                  padding: '14px',
                  backgroundColor: 'rgba(255,255,255,0.05)',
                  border: '1px solid rgba(255,255,255,0.1)',
                  borderRadius: '10px',
                  color: 'white',
                  fontSize: '14px',
                  cursor: 'pointer'
                }}
              >
                {Object.entries(zonasData).map(([key, data]) => (
                  <option key={key} value={key} style={{ backgroundColor: '#1e293b' }}>{data.nombre}</option>
                ))}
              </select>
              <span style={{ color: '#64748b', fontWeight: '700', fontSize: '18px' }}>VS</span>
              <select
                value={zonaCompare2}
                onChange={(e) => setZonaCompare2(e.target.value)}
                style={{
                  padding: '14px',
                  backgroundColor: 'rgba(255,255,255,0.05)',
                  border: '1px solid rgba(255,255,255,0.1)',
                  borderRadius: '10px',
                  color: 'white',
                  fontSize: '14px',
                  cursor: 'pointer'
                }}
              >
                {Object.entries(zonasData).map(([key, data]) => (
                  <option key={key} value={key} style={{ backgroundColor: '#1e293b' }}>{data.nombre}</option>
                ))}
              </select>
            </div>

            {/* Comparación */}
            <div style={{
              background: 'rgba(255,255,255,0.03)',
              borderRadius: '16px',
              padding: '24px',
              border: '1px solid rgba(255,255,255,0.08)'
            }}>
              {[
                { label: 'Cap Rate', key: 'capRate', suffix: '%', higherBetter: true },
                { label: 'Vacancia', key: 'vacancia', suffix: '%', higherBetter: false },
                { label: 'Precio/m²', key: 'precio', prefix: '$', higherBetter: false },
                { label: 'Alquiler/m²', key: 'alquiler', prefix: '$', higherBetter: true },
                { label: 'Mora', key: 'mora', suffix: '%', higherBetter: false },
              ].map(({ label, key, suffix, prefix, higherBetter }) => {
                const v1 = zonasData[zonaCompare1][key];
                const v2 = zonasData[zonaCompare2][key];
                const winner1 = higherBetter ? v1 > v2 : v1 < v2;
                const winner2 = higherBetter ? v2 > v1 : v2 < v1;

                return (
                  <div key={key} style={{ 
                    display: 'grid', 
                    gridTemplateColumns: '1fr auto 1fr', 
                    gap: '12px', 
                    padding: '14px 0',
                    borderBottom: '1px solid rgba(255,255,255,0.06)'
                  }}>
                    <div style={{ textAlign: 'right' }}>
                      <span style={{ 
                        fontSize: '18px', 
                        fontWeight: '600', 
                        color: winner1 ? '#4ade80' : '#64748b' 
                      }}>
                        {prefix}{v1}{suffix} {winner1 && '✓'}
                      </span>
                    </div>
                    <div style={{ textAlign: 'center', color: '#64748b', fontSize: '13px' }}>{label}</div>
                    <div style={{ textAlign: 'left' }}>
                      <span style={{ 
                        fontSize: '18px', 
                        fontWeight: '600', 
                        color: winner2 ? '#4ade80' : '#64748b' 
                      }}>
                        {winner2 && '✓ '}{prefix}{v2}{suffix}
                      </span>
                    </div>
                  </div>
                );
              })}

              {/* Ganador */}
              <div style={{ textAlign: 'center', marginTop: '20px' }}>
                <p style={{ color: '#64748b', fontSize: '13px', margin: '0 0 8px 0' }}>Recomendación por Cap Rate</p>
                <div style={{
                  display: 'inline-block',
                  padding: '12px 28px',
                  backgroundColor: '#10b981',
                  borderRadius: '100px'
                }}>
                  <span style={{ fontWeight: '700', color: 'white' }}>
                    🏆 {zonasData[zonaCompare1].capRate > zonasData[zonaCompare2].capRate 
                      ? zonasData[zonaCompare1].nombre 
                      : zonasData[zonaCompare2].nombre}
                  </span>
                </div>
              </div>
            </div>
          </div>
        )}

        {/* ==================== TAB: MORA ==================== */}
        {tab === 'mora' && (
          <div>
            <h2 style={{ textAlign: 'center', fontSize: '24px', margin: '0 0 8px 0' }}>⚠️ Mapa de Mora</h2>
            <p style={{ textAlign: 'center', color: '#64748b', marginBottom: '24px' }}>Riesgo hipotecario por zona</p>

            {/* Alerta */}
            <div style={{
              background: 'rgba(239, 68, 68, 0.1)',
              borderRadius: '12px',
              padding: '16px',
              border: '1px solid rgba(239, 68, 68, 0.2)',
              marginBottom: '20px'
            }}>
              <p style={{ color: '#f87171', fontSize: '14px', margin: 0, lineHeight: '1.6' }}>
                <strong>🔴 Zonas con mora &gt;10%</strong> = Mayor probabilidad de remates y bienes adjudicados en 2026
              </p>
            </div>

            {/* Ranking de mora */}
            <div style={{
              background: 'rgba(255,255,255,0.03)',
              borderRadius: '12px',
              padding: '20px',
              border: '1px solid rgba(255,255,255,0.06)'
            }}>
              <h3 style={{ margin: '0 0 16px 0', fontSize: '16px' }}>📊 Ranking por Mora Hipotecaria</h3>
              
              {Object.entries(zonasData)
                .sort((a, b) => b[1].mora - a[1].mora)
                .map(([key, data], index) => {
                  const moraColor = data.mora >= 10 ? '#ef4444' : data.mora >= 7 ? '#f59e0b' : '#22c55e';
                  const barWidth = (data.mora / 15) * 100;
                  
                  return (
                    <div key={key} style={{ marginBottom: '16px' }}>
                      <div style={{ display: 'flex', justifyContent: 'space-between', marginBottom: '6px' }}>
                        <span style={{ fontSize: '14px', color: 'white' }}>
                          {index + 1}. {data.nombre}
                        </span>
                        <span style={{ fontSize: '14px', fontWeight: '700', color: moraColor }}>
                          {data.mora}%
                        </span>
                      </div>
                      <div style={{
                        height: '8px',
                        backgroundColor: 'rgba(255,255,255,0.1)',
                        borderRadius: '4px',
                        overflow: 'hidden'
                      }}>
                        <div style={{
                          width: `${barWidth}%`,
                          height: '100%',
                          backgroundColor: moraColor,
                          borderRadius: '4px',
                          transition: 'width 0.5s ease'
                        }}></div>
                      </div>
                    </div>
                  );
                })}
            </div>

            {/* Interpretación */}
            <div style={{
              marginTop: '20px',
              background: 'rgba(255,255,255,0.03)',
              borderRadius: '12px',
              padding: '20px',
              border: '1px solid rgba(255,255,255,0.06)'
            }}>
              <h3 style={{ margin: '0 0 12px 0', fontSize: '16px' }}>💡 ¿Qué significa?</h3>
              <div style={{ display: 'flex', flexDirection: 'column', gap: '12px' }}>
                <div style={{ display: 'flex', alignItems: 'center', gap: '12px' }}>
                  <div style={{ width: '12px', height: '12px', borderRadius: '50%', backgroundColor: '#ef4444' }}></div>
                  <span style={{ color: '#cbd5e1', fontSize: '14px' }}><strong style={{ color: '#f87171' }}>&gt;10%</strong> — Alta probabilidad de remates</span>
                </div>
                <div style={{ display: 'flex', alignItems: 'center', gap: '12px' }}>
                  <div style={{ width: '12px', height: '12px', borderRadius: '50%', backgroundColor: '#f59e0b' }}></div>
                  <span style={{ color: '#cbd5e1', fontSize: '14px' }}><strong style={{ color: '#fbbf24' }}>7-10%</strong> — Riesgo moderado</span>
                </div>
                <div style={{ display: 'flex', alignItems: 'center', gap: '12px' }}>
                  <div style={{ width: '12px', height: '12px', borderRadius: '50%', backgroundColor: '#22c55e' }}></div>
                  <span style={{ color: '#cbd5e1', fontSize: '14px' }}><strong style={{ color: '#4ade80' }}>&lt;7%</strong> — Mercado estable</span>
                </div>
              </div>
            </div>

            {/* Insight */}
            <div style={{
              marginTop: '20px',
              background: 'linear-gradient(135deg, rgba(139, 92, 246, 0.1) 0%, rgba(139, 92, 246, 0.05) 100%)',
              borderRadius: '12px',
              padding: '20px',
              border: '1px solid rgba(139, 92, 246, 0.2)'
            }}>
              <h3 style={{ color: '#a78bfa', margin: '0 0 8px 0', fontSize: '15px' }}>🎯 Oportunidad Contrarian</h3>
              <p style={{ color: '#94a3b8', fontSize: '14px', margin: 0, lineHeight: '1.6' }}>
                Las zonas con <strong style={{ color: 'white' }}>alta mora + alto Cap Rate</strong> (Sur, Este) 
                ofrecen oportunidades de compra de adjudicados a descuento. 
                Bienes adjudicados actuales: <strong style={{ color: '#a78bfa' }}>$183M</strong> y creciendo.
              </p>
            </div>
          </div>
        )}

        {/* ==================== TAB: PREDICCIONES ==================== */}
        {tab === 'predicciones' && (
          <div>
            <h2 style={{ textAlign: 'center', fontSize: '24px', margin: '0 0 8px 0' }}>🔮 Predicciones 2026</h2>
            <p style={{ textAlign: 'center', color: '#64748b', marginBottom: '32px' }}>Nos jugamos el cuello. Verificá en 6 meses.</p>

            {/* Timeline */}
            <div style={{ position: 'relative', paddingLeft: '32px' }}>
              <div style={{
                position: 'absolute',
                left: '10px',
                top: '0',
                bottom: '0',
                width: '3px',
                background: 'linear-gradient(180deg, #3b82f6 0%, #8b5cf6 50%, #ec4899 100%)',
                borderRadius: '2px'
              }}></div>

              {[
                { texto: "Stock adjudicados superará $200M", actual: "$183M", fecha: "Q2 2026" },
                { texto: "Mora hipotecaria > 4.5%", actual: "3.9%", fecha: "Q2 2026" },
                { texto: "Precio real estabiliza $1,300-$1,400/m²", actual: "$1,329/m²", fecha: "Q1 2026" },
                { texto: "Proyectos de casas < 10 en 2026", actual: "8 (2025)", fecha: "Dic 2026" },
                { texto: "Equipetrol vacancia > 35%", actual: "~30%", fecha: "Q2 2026" }
              ].map((pred, i) => (
                <div key={i} style={{ position: 'relative', marginBottom: '16px' }}>
                  <div style={{
                    position: 'absolute',
                    left: '-28px',
                    width: '16px',
                    height: '16px',
                    borderRadius: '50%',
                    backgroundColor: ['#3b82f6', '#6366f1', '#8b5cf6', '#a855f7', '#ec4899'][i],
                    border: '3px solid #0a0f1a'
                  }}></div>

                  <div style={{
                    background: 'rgba(255,255,255,0.03)',
                    borderRadius: '10px',
                    padding: '16px',
                    border: '1px solid rgba(255,255,255,0.06)'
                  }}>
                    <h4 style={{ margin: '0 0 8px 0', fontSize: '14px', color: 'white' }}>{pred.texto}</h4>
                    <div style={{ display: 'flex', gap: '16px', fontSize: '12px' }}>
                      <span style={{ color: '#64748b' }}>Actual: <strong style={{ color: '#cbd5e1' }}>{pred.actual}</strong></span>
                      <span style={{ color: '#60a5fa' }}>Verificar: <strong>{pred.fecha}</strong></span>
                    </div>
                  </div>
                </div>
              ))}
            </div>

            <div style={{
              marginTop: '24px',
              padding: '20px',
              background: 'rgba(59, 130, 246, 0.1)',
              borderRadius: '12px',
              border: '1px solid rgba(59, 130, 246, 0.2)',
              textAlign: 'center'
            }}>
              <p style={{ margin: 0, fontSize: '14px', color: '#93c5fd' }}>
                📢 Guardá esta página y volvé en 6 meses
              </p>
              <p style={{ margin: '8px 0 0 0', fontSize: '12px', color: '#64748b' }}>
                Fuente: Citrino Capitales Inmobiliarios • Dic 2025
              </p>
            </div>
          </div>
        )}

      </main>

      {/* Footer */}
      <footer style={{
        padding: '20px',
        textAlign: 'center',
        borderTop: '1px solid rgba(255,255,255,0.06)'
      }}>
        <p style={{ color: '#475569', fontSize: '12px', margin: 0 }}>
          Datos: Citrino Capitales Inmobiliarios (Dic 2025)
        </p>
        <p style={{ color: '#334155', fontSize: '11px', margin: '6px 0 0 0' }}>
          Herramienta educativa • No constituye asesoría de inversión
        </p>
      </footer>
    </div>
  );
}

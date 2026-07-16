<svg width="380" height="480" viewBox="0 0 380 480" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <title>HUD Scanning Profile - @miikeepp</title>

  <defs>
    <!-- Recorte con esquinas tecnológicas (cortadas) para la foto -->
    <clipPath id="photoClip">
      <path d="M84,80 L296,80 L320,104 L320,316 L296,340 L84,340 L60,316 L60,104 Z"/>
    </clipPath>

    <!-- Glow para la línea de escaneo -->
    <filter id="scanGlow" x="-50%" y="-50%" width="200%" height="200%">
      <feGaussianBlur stdDeviation="4" result="blur"/>
      <feMerge>
        <feMergeNode in="blur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>

    <!-- Glow pulsante para el marco -->
    <filter id="frameGlow" x="-50%" y="-50%" width="200%" height="200%">
      <feGaussianBlur stdDeviation="2" result="blur">
        <animate attributeName="stdDeviation" values="1;4;1" dur="2.4s" repeatCount="indefinite"/>
      </feGaussianBlur>
      <feMerge>
        <feMergeNode in="blur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>

    <!-- Gradiente horizontal para la línea de escaneo -->
    <linearGradient id="scanGrad" x1="0" y1="0" x2="1" y2="0">
      <stop offset="0%" stop-color="#00F5FF" stop-opacity="0"/>
      <stop offset="50%" stop-color="#7DF9FF" stop-opacity="0.95"/>
      <stop offset="100%" stop-color="#00F5FF" stop-opacity="0"/>
    </linearGradient>

    <!-- Patrón sutil de scanlines -->
    <pattern id="scanlinesPattern" width="6" height="6" patternUnits="userSpaceOnUse">
      <rect width="6" height="6" fill="none"/>
      <line x1="0" y1="0" x2="6" y2="0" stroke="#00F5FF" stroke-opacity="0.08" stroke-width="1"/>
    </pattern>
  </defs>

  <!-- ===================== MARCO EXTERIOR HUD ===================== -->
  <g filter="url(#frameGlow)">
    <path d="M82,74 L298,74 L326,102 L326,318 L298,346 L82,346 L54,318 L54,102 Z"
          fill="none" stroke="#00BFFF" stroke-width="2">
      <animate attributeName="stroke-opacity" values="0.35;1;0.35" dur="2.4s" repeatCount="indefinite"/>
    </path>
  </g>

  <!-- Esquinas técnicas tipo bracket -->
  <g stroke="#00F5FF" stroke-width="3" fill="none" stroke-linecap="round">
    <path d="M40,84 L40,58 L66,58">
      <animate attributeName="stroke-opacity" values="1;0.3;1" dur="1.8s" repeatCount="indefinite"/>
    </path>
    <path d="M314,58 L340,58 L340,84">
      <animate attributeName="stroke-opacity" values="0.3;1;0.3" dur="1.8s" begin="0.3s" repeatCount="indefinite"/>
    </path>
    <path d="M340,336 L340,362 L314,362">
      <animate attributeName="stroke-opacity" values="1;0.3;1" dur="1.8s" begin="0.6s" repeatCount="indefinite"/>
    </path>
    <path d="M66,362 L40,362 L40,336">
      <animate attributeName="stroke-opacity" values="0.3;1;0.3" dur="1.8s" begin="0.9s" repeatCount="indefinite"/>
    </path>
  </g>

  <!-- Radar giratorio decorativo (elemento HUD) -->
  <g transform="translate(326,102)">
    <circle r="10" fill="none" stroke="#7DF9FF" stroke-width="1.5"
            stroke-dasharray="16 40" stroke-opacity="0.8">
      <animateTransform attributeName="transform" type="rotate"
                         from="0 0 0" to="360 0 0" dur="3s" repeatCount="indefinite"/>
    </circle>
  </g>

  <!-- Ticks pequeños en los bordes del marco -->
  <g fill="#00F5FF">
    <circle cx="54" cy="210" r="3">
      <animate attributeName="opacity" values="1;0.15;1" dur="1.2s" repeatCount="indefinite"/>
    </circle>
    <circle cx="326" cy="210" r="3">
      <animate attributeName="opacity" values="0.15;1;0.15" dur="1.2s" repeatCount="indefinite"/>
    </circle>
    <circle cx="190" cy="74" r="3">
      <animate attributeName="opacity" values="1;0.15;1" dur="1.5s" repeatCount="indefinite"/>
    </circle>
  </g>

  <!-- ===================== FOTO DE PERFIL ===================== -->
  <image href="https://github.com/miikeepp.png"
         xlink:href="https://github.com/miikeepp.png"
         x="60" y="80" width="260" height="260"
         preserveAspectRatio="xMidYMid slice"
         clip-path="url(#photoClip)"/>

  <!-- Scanlines sutiles sobre la foto -->
  <rect x="60" y="80" width="260" height="260" fill="url(#scanlinesPattern)" clip-path="url(#photoClip)"/>

  <!-- Línea de escaneo con glow -->
  <rect x="60" y="80" width="260" height="6" fill="url(#scanGrad)"
        filter="url(#scanGlow)" clip-path="url(#photoClip)">
    <animate attributeName="y" values="80;340;80" keyTimes="0;0.5;1"
             dur="2.6s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values="0.9;0.9;0" keyTimes="0;0.9;1"
             dur="2.6s" repeatCount="indefinite"/>
  </rect>

  <!-- Overlay leve de tinte cyan que respira sobre la foto -->
  <rect x="60" y="80" width="260" height="260" fill="#00F5FF" clip-path="url(#photoClip)">
    <animate attributeName="opacity" values="0.03;0.09;0.03" dur="2.6s" repeatCount="indefinite"/>
  </rect>

  <!-- ===================== TEXTO ESTILO SISTEMA ===================== -->
  <g font-family="Consolas, 'Courier New', monospace" letter-spacing="2">
    <text x="190" y="378" text-anchor="middle" font-size="15" fill="#00F5FF">
      SCANNING...
      <animate attributeName="opacity" values="1;0.35;1" dur="1.4s" repeatCount="indefinite"/>
    </text>

    <circle cx="112" cy="401" r="4" fill="#7DF9FF">
      <animate attributeName="opacity" values="1;0.2;1" dur="1s" repeatCount="indefinite"/>
    </circle>
    <text x="122" y="406" font-size="13" fill="#00BFFF">STATUS: ONLINE</text>

    <text x="190" y="432" text-anchor="middle" font-size="12" fill="#7DF9FF" letter-spacing="1">
      USER: @miikeepp
    </text>

    <!-- Línea separadora HUD -->
    <line x1="80" y1="415" x2="300" y2="415" stroke="#00F5FF" stroke-width="1" stroke-opacity="0.25"/>
  </g>
</svg>
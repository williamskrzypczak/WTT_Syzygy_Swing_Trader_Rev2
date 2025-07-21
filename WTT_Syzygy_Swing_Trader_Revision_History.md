# WTT Syzygy Swing Trader - Consolidated Revision History

## Core Features & Enhancements

- **Swing High/Low Detection & Trend Structure**
  - Uses 7-bar lookback for pivots (`ta.pivothigh`, `ta.pivotlow`).
  - Trend status labels: Uptrend, Downtrend, Sideways.
  - Horizontal and trend lines for structure visualization.
  - Structure symbols (↗️, ↘️, ↔️) on lines.

- **Breakout & Breach System**
  - Dynamic color-changing lines: lime green (bullish), deep pink (bearish).
  - Synchronized alerts for breakouts (visual and alertcondition).
  - Debug visual indicators (plotshape) for breakout logic (toggleable).
  - Persistent profit target and stop loss lines, removed only on breach.

- **Risk-Reward & Trade Management**
  - Dynamic R:R table in upper right, showing live risk/reward, pip distance, and trade status.
  - Stop loss line and label ("SL"), with trailing stop ("TS") and partial profit-taking logic.
  - Automatic removal of profit target/stop loss lines when hit.
  - Position sizing based on account size and risk per trade.
  - Success rate and partial success tracking, including profit factor.
  - Calculation and display of pip distance from entry to target.

- **Visual & Usability Enhancements**
  - Vibrant color scheme: lime green and deep pink (RGB).
  - Table theme toggle (light/dark), with conditional colors.
  - Toggle for strategy rules visibility in the table.
  - Visually appealing HTML cheat sheet with usage guide and pro tips.

- **Alerts & Notifications**
  - `alertcondition` for bullish/bearish breakouts, trailing stop activation, and test/debug.
  - Alerts fire exactly when line color changes (no lag).

## Major Bug Fixes & Robustness

- **NaN/Error Handling**
  - Division by zero prevention in R:R and position sizing.
  - Table displays "na" for invalid calculations, never "NaN".
  - Robust checks for valid swing points and risk values.

- **Line & Label Persistence**
  - Fixed profit target and stop loss lines moving every bar; now persist until next breach.
  - Ensured labels ("PT", "SL", "TS") only appear on current lines and are removed with lines.

- **Performance & Logic**
  - Removed unused variables and code blocks for efficiency.
  - Improved breach detection logic to use `close` for reliability.
  - Refined alert logic to separate calculation from label display.

## Project Evolution & Naming

- Originally: `WTT_TrendTracker.pine` → `WTT_Syzygy_Swing_Trader.pine`.
- Revision history and documentation renamed accordingly.
- Cheat sheet and all documentation updated to match new project name and features.

## Usage & Best Practices

- Enter trades on actual breakouts (not near levels).
- Use persistent lines for clear entry, stop, and target.
- Follow table and cheat sheet for live trade management and strategy rules.

## Recent Updates (R1.28)

- **Enhanced Table Features**
  - Added RSI and Volume tracking rows with color-coded status indicators
  - RSI displays: Overbought (red), Oversold (green), Bullish (green), Bearish (red), Neutral (orange)
  - Volume displays: Weak (red), Normal (orange), High (green) with numerical ratios
  - Added table toggle functionality to show/hide entire risk-reward table
  - Removed unused "Risk Per Trade Percentage" and "Account Size" inputs for cleaner interface

- **Code Optimization**
  - Removed unused position sizing calculations and variables
  - Streamlined input parameters to only include actively used settings
  - Improved code efficiency by eliminating dead code paths

## Future Enhancements (Potential)
- Multi-timeframe analysis
- Advanced breakout filters
- Custom profit target ratios
- Additional technical indicators

---

**This revision history is consolidated and current through R1.28. For detailed per-version changes, refer to previous logs or commit history.** 
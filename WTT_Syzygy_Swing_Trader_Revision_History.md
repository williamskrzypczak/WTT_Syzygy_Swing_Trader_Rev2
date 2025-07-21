# WTT Syzygy Swing Trader - Revision History

## R1.0 - R1.27: Foundation & Core Features

The indicator evolved from basic swing detection to a comprehensive swing trading system. Key milestones included implementing 7-bar lookback pivot detection, dynamic color-changing breakout lines (lime green for bullish, deep pink for bearish), and persistent profit target/stop loss lines. The risk-reward table was added with live calculations, success rate tracking, and partial profit-taking logic. Visual enhancements included vibrant color schemes, theme toggles, and debug indicators. Alert systems were refined using `alertcondition` for reliable breakout notifications.

## R1.28: Enhanced Table & Interface Optimization

Added RSI and Volume tracking to the risk-reward table with color-coded status indicators. RSI shows Overbought (red), Oversold (green), Bullish (green), Bearish (red), and Neutral (orange) states. Volume displays Weak (red), Normal (orange), and High (green) status. Implemented table toggle functionality and removed unused "Risk Per Trade Percentage" and "Account Size" inputs for a cleaner interface. Streamlined code by eliminating unused position sizing calculations and variables.

## R1.29: RSI Removal & Volume Enhancement

Completely removed all RSI functionality from the indicator to simplify the codebase and focus on core swing trading features. Replaced RSI input with a dedicated "Show Volume in Table" toggle. Enhanced volume display to show both status (High/Normal/Weak) and actual volume numbers (e.g., "High (1250000)") for better quantitative analysis. Reduced table size from 10 to 9 rows when volume is enabled, streamlining the interface while maintaining all essential trading information.

## Future Revisions (R2.0+)

All future updates will be numbered R2.0 and above, with consolidated change descriptions in paragraph format for better readability and maintenance.

---

**Current version: R1.29 | Next version: R2.0** 
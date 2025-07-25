# WTT Syzygy Swing Trader - Revision History

## R1.0 - R1.27: Foundation & Core Features

The indicator evolved from basic swing detection to a comprehensive swing trading system. Key milestones included implementing 7-bar lookback pivot detection, dynamic color-changing breakout lines (lime green for bullish, deep pink for bearish), and persistent profit target/stop loss lines. The risk-reward table was added with live calculations, success rate tracking, and partial profit-taking logic. Visual enhancements included vibrant color schemes, theme toggles, and debug indicators. Alert systems were refined using `alertcondition` for reliable breakout notifications.

## R1.28: Enhanced Table & Interface Optimization

Added RSI and Volume tracking to the risk-reward table with color-coded status indicators. RSI shows Overbought (red), Oversold (green), Bullish (green), Bearish (red), and Neutral (orange) states. Volume displays Weak (red), Normal (orange), and High (green) status. Implemented table toggle functionality and removed unused "Risk Per Trade Percentage" and "Account Size" inputs for a cleaner interface. Streamlined code by eliminating unused position sizing calculations and variables.

## R1.29: RSI Removal & Volume Enhancement

Completely removed all RSI functionality from the indicator to simplify the codebase and focus on core swing trading features. Replaced RSI input with a dedicated "Show Volume in Table" toggle. Enhanced volume display to show both status (High/Normal/Weak) and actual volume numbers (e.g., "High (1250000)") for better quantitative analysis. Reduced table size from 10 to 9 rows when volume is enabled, streamlining the interface while maintaining all essential trading information.

## R1.30: Alert Enhancements & Code Organization

Enhanced alert system with comprehensive trade information including symbol, current price, opposite swing price (suggested stop loss), and profit target. Removed test alerts and alertcondition() calls to streamline the alert system. Reorganized code structure with consistent 2-line spacing between major sections for improved readability and maintenance. Moved debug visual indicators to the bottom of the script for better logical organization.

## R1.31: Trailing Stop Alert Enhancement & Volume Calculation Improvement

Enhanced trailing stop alert to include strategic position management suggestion: "According to the indicator's strategy, this is a suggested point to close 50% (half) of your position." Improved volume calculation method from simple ratio comparison to statistical standard deviation analysis using z-scores. New volume classification uses 20-period SMA and standard deviation to determine High (>1.0 z-score), Weak (<-1.0 z-score), and Normal (-1.0 to 1.0 z-score) volume status, providing more statistically sound and adaptive volume analysis.

## R1.32: Volume Alert System Implementation

Added comprehensive volume alert system with dual functionality for both high and low volume detection. High volume alerts trigger when volume exceeds 1.0 z-score above 20-period average, indicating increased market activity and potential trend continuation or reversal. Low volume alerts trigger when volume falls below -1.0 z-score, indicating decreased market activity and potential consolidation or indecision. Both alerts include detailed information: symbol, current price, actual volume in thousands, z-score value, and market context. Alerts are conditionally activated only when "Show Volume in Table" option is enabled, maintaining consistency with existing volume analysis features. Implementation reuses existing volume calculations for optimal performance without additional computational overhead.

## R1.33: Volume Filter for Breakouts

Implemented optional volume filtering system for swing breakouts to improve signal quality and reduce false breakouts. Added "Enable Volume Filter for Breakouts" toggle and configurable "Volume Filter Threshold" input (z-score based, range -2.0 to 2.0). When enabled, breakouts only trigger when volume z-score meets or exceeds the specified threshold. Default threshold of 0.0 requires above-average volume for breakout confirmation. Volume filter applies to both long and short breakouts, as well as breakout alerts. Added visual feedback in the risk-reward table showing filter status (PASS/BLOCK) and current threshold when volume filtering is active. Table dynamically expands to accommodate the new volume filter status row. This feature allows traders to focus on high-conviction breakouts with institutional support while maintaining the flexibility to disable filtering when desired.

## R1.34: Streamlined Volume Alerts

Removed standalone high and low volume alerts to eliminate redundancy with the integrated volume filtering system. Since volume filtering is now built into the breakout signals and alerts, separate volume alerts were creating unnecessary noise and duplicate notifications. The volume filter system provides more targeted and actionable alerts by only notifying when volume conditions meet the specified threshold for actual breakout opportunities. This streamlining improves the user experience by reducing alert fatigue and focusing on high-probability trading setups.

## R1.35: Volume Filter Validation Fix

Fixed critical bug in volume filtering logic where alerts were not properly respecting the volume filter threshold setting. Enhanced validation in both main breakout detection and alert conditions to ensure proper threshold checking. Added explicit validation for volume_filter_threshold to prevent alerts from triggering when threshold is invalid or volume z-score doesn't meet the specified requirement. The fix ensures that when volume filtering is enabled, alerts will only trigger when the volume z-score meets or exceeds the user-defined threshold, providing more accurate and filtered breakout signals.

## R1.36: Table Consolidation & Optimization

Streamlined the risk-reward table by consolidating related information into fewer, more efficient rows. Combined Signal & R:R Ratio, Entry & Pip Distance, Position & PM Status, and Volume & Filter into single rows with pipe-separated values. Reduced table size from 9-10 rows to 5-6 rows while maintaining all essential trading information. Improved readability and reduced visual clutter while preserving functionality. Table now displays more information in less space, making it easier to scan and interpret at a glance.

## R1.37: RSI Integration & Enhanced Technical Analysis

Added comprehensive RSI (Relative Strength Index) integration to the HUD table with configurable length parameter (default 14 periods). RSI display includes both numerical value and status classification: Overbought (≥70), Oversold (≤30), Bullish (>50), Bearish (<50), and Neutral (=50). Color-coded status indicators provide instant visual feedback: red for overbought/bearish, green for oversold/bullish, orange for neutral. Added "Show RSI in Table" toggle for optional display and "RSI Length" input for customization. Table dynamically adjusts size to accommodate RSI row when enabled, providing traders with additional momentum analysis alongside existing volume and position management data. Updated default settings: Light Table Theme now defaults to false (dark theme), and Volume Filter for Breakouts now defaults to true for improved signal quality.

## R1.38: RSI Visual Chart Indicators

Added visual RSI overbought/oversold indicators directly on the price chart for enhanced technical analysis. Implemented tiny circular dots that appear when RSI reaches extreme levels: red dots above price bars when RSI ≥ 70 (overbought) and green dots below price bars when RSI ≤ 30 (oversold). These visual indicators provide instant chart-based confirmation of potential reversal points, complementing the existing RSI table display. The dots are conditionally displayed only when "Show RSI in Table" is enabled, maintaining consistency with existing RSI functionality. This enhancement helps traders quickly identify overbought and oversold conditions directly on the chart without needing to reference the HUD table, improving the overall trading experience and decision-making process.

## R1.39: RSI Loading Performance Fix

Fixed critical performance issue where RSI values in the HUD table were loading slowly when switching between trading instruments. The problem was caused by RSI calculation being restricted to only the last bar (`barstate.islast`) while RSI dots were calculating continuously on every bar. Resolved by consolidating RSI calculation into a single, continuous calculation that runs on every bar and is shared between both the table display and visual dots. This optimization ensures RSI values load immediately when switching instruments, providing consistent and responsive RSI analysis across all chart interactions. The fix maintains all existing functionality while dramatically improving the user experience for multi-instrument trading scenarios.

## R1.40: Swing Line Length Optimization

Optimized horizontal swing line length for improved chart clarity and reduced visual clutter. Reduced swing line extension from 50 bars to 20 bars forward from the swing point, making the lines 60% shorter while maintaining clear visual reference for swing levels. This enhancement provides better chart readability by reducing line overlap and clutter, particularly on longer timeframes or when multiple swing points are present. The lines continue to function with full color-changing behavior (lime green for bullish breakouts, deep pink for bearish breakdowns) and maintain all existing breakout detection and alert functionality. This visual optimization improves the overall trading experience by providing cleaner, more focused swing level visualization.

## Future Revisions (R2.0+)

All future updates will be numbered R2.0 and above, with consolidated change descriptions in paragraph format for better readability and maintenance.

---

**Current version: R1.40 | Next version: R2.0** 
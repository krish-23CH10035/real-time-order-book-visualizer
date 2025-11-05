# Deployment Guide

## Quick Start Guide

Follow these steps to get your project up and running:

### 1. Initial Setup

```bash
# Create the Next.js project
npx create-next-app@latest order-book-visualizer --typescript --tailwind --app --eslint

# Navigate to the project
cd order-book-visualizer

# Install Zustand
npm install zustand
```

### 2. File Structure Setup

Create the following directory structure:

```
src/
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   └── globals.css
├── components/
│   ├── OrderBook/
│   │   ├── OrderBook.tsx
│   │   ├── OrderBookRow.tsx
│   │   ├── BidsList.tsx
│   │   ├── AsksList.tsx
│   │   └── Spread.tsx
│   ├── RecentTrades/
│   │   ├── RecentTrades.tsx
│   │   └── TradeRow.tsx
│   └── ConnectionStatus.tsx
├── hooks/
│   ├── useBinanceSocket.ts
│   └── useOrderBook.ts
├── store/
│   └── orderBookStore.ts
├── types/
│   └── binance.ts
└── utils/
    └── orderBookHelpers.ts
```

### 3. Copy All Files

Copy each file I provided into its respective location. Here's the checklist:

#### Type Definitions
- [ ] `src/types/binance.ts`

#### Utilities
- [ ] `src/utils/orderBookHelpers.ts`

#### Hooks
- [ ] `src/hooks/useBinanceSocket.ts`
- [ ] `src/hooks/useOrderBook.ts`

#### Store
- [ ] `src/store/orderBookStore.ts`

#### Components - Order Book
- [ ] `src/components/OrderBook/OrderBook.tsx`
- [ ] `src/components/OrderBook/OrderBookRow.tsx`
- [ ] `src/components/OrderBook/BidsList.tsx`
- [ ] `src/components/OrderBook/AsksList.tsx`
- [ ] `src/components/OrderBook/Spread.tsx`

#### Components - Recent Trades
- [ ] `src/components/RecentTrades/RecentTrades.tsx`
- [ ] `src/components/RecentTrades/TradeRow.tsx`

#### Other Components
- [ ] `src/components/ConnectionStatus.tsx`

#### App Files
- [ ] `src/app/page.tsx`
- [ ] `src/app/layout.tsx`
- [ ] `src/app/globals.css`

#### Configuration Files
- [ ] `package.json` (update dependencies)
- [ ] `tsconfig.json`
- [ ] `tailwind.config.ts`
- [ ] `next.config.js`
- [ ] `postcss.config.js`
- [ ] `.eslintrc.json`
- [ ] `.gitignore`

#### Documentation
- [ ] `README.md`

### 4. Run Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### 5. Test the Application

Verify the following:
- [ ] WebSocket connection status shows "Connected"
- [ ] Order book displays bid/ask prices
- [ ] Depth bars are visible
- [ ] Recent trades appear and flash
- [ ] Spread is calculated correctly
- [ ] No console errors

### 6. Build for Production

```bash
npm run build
npm start
```

Test the production build locally before deploying.

## Deploying to Vercel

### Method 1: Vercel CLI (Recommended)

```bash
# Install Vercel CLI globally
npm install -g vercel

# Login to Vercel
vercel login

# Deploy to preview
vercel

# Deploy to production
vercel --prod
```

### Method 2: GitHub Integration

1. Push your code to GitHub:
```bash
git init
git add .
git commit -m "Initial commit: Real-time Order Book Visualizer"
git branch -M main
git remote add origin https://github.com/2CentsCapitalHR/valura-frontend-assignment-krish-23CH10035.git
git push -u origin main
```

2. Go to [Vercel Dashboard](https://vercel.com/dashboard)
3. Click "Add New Project"
4. Import your GitHub repository
5. Configure project:
   - Framework Preset: Next.js
   - Root Directory: `./`
   - Build Command: `npm run build`
   - Output Directory: `.next`
6. Click "Deploy"

### Method 3: Vercel Web UI (Drag & Drop)

1. Build the project locally:
```bash
npm run build
```

2. Go to [Vercel](https://vercel.com)
3. Drag and drop your project folder
4. Vercel will automatically detect Next.js and deploy

## Post-Deployment

### 1. Test Live Application

- [ ] Visit your Vercel URL
- [ ] Check WebSocket connection works
- [ ] Verify all features function correctly
- [ ] Test on different devices/browsers
- [ ] Check performance (60fps)

### 2. Update README

Add your live demo link to the README:
```markdown
🔗 **[Live Demo](https://your-app-name.vercel.app)**
```

### 3. Submit Assignment

1. Fill out the Google Form with:
   - GitHub repository link
   - Live demo URL (Vercel)
   - Any additional notes

2. Verify all links work before submitting

## Troubleshooting

### WebSocket Connection Issues

**Problem**: "Failed to connect" error

**Solution**:
- Check browser console for specific errors
- Verify internet connection
- Try in incognito mode (disable extensions)
- Check if Binance WebSocket is accessible in your region

### Build Errors

**Problem**: TypeScript errors during build

**Solution**:
```bash
# Clear cache and rebuild
rm -rf .next
rm -rf node_modules
npm install
npm run build
```

### Vercel Deployment Fails

**Problem**: Build fails on Vercel

**Solution**:
- Check build logs in Vercel dashboard
- Ensure all dependencies are in `package.json`
- Verify no environment-specific code
- Test local build with `npm run build`

### Performance Issues

**Problem**: Laggy UI or slow updates

**Solution**:
- Check if too many rows are being rendered
- Verify React.memo is used on components
- Check browser performance in DevTools
- Ensure WebSocket isn't receiving too much data

## Environment-Specific Notes

### No Environment Variables Needed

This project doesn't require any API keys or environment variables. It uses the public Binance WebSocket API.

### CORS and WebSocket

- The Binance WebSocket API supports browser connections
- No CORS issues expected
- Works in all modern browsers

## Performance Checklist

Before deployment, verify:
- [ ] No console errors or warnings
- [ ] Smooth 60fps scrolling
- [ ] Order book updates without lag
- [ ] Memory usage is stable (check DevTools)
- [ ] No memory leaks over time
- [ ] Lighthouse score > 90

## Security Considerations

- No sensitive data stored
- No API keys required
- All data is public market information
- Client-side only (no server endpoints)

## Additional Resources

- [Next.js Deployment Docs](https://nextjs.org/docs/deployment)
- [Vercel Documentation](https://vercel.com/docs)
- [Binance WebSocket API](https://binance-docs.github.io/apidocs/spot/en/#websocket-market-streams)

---

**Good luck with your deployment! 🚀**

# Beauty Scan 📷

A beautiful barcode scanning app for USA beauty products, built with Expo and React Native. Scan product barcodes to instantly view detailed product information including name, brand, category, ingredients, and more.

## Features

- 📷 **Barcode Scanning**: Scan product barcodes using your device's camera
- 🎨 **Baby Pink Theme**: Beautiful, modern UI with a baby pink color scheme
- 📦 **Product Details**: View comprehensive product information including:
  - Product name and brand
  - Category and size
  - Price information
  - Ingredients list
  - Product images
- 🔍 **Multiple Barcode Formats**: Supports EAN-13, EAN-8, UPC-A, UPC-E, Code128, and Code39
- 🌐 **Free API Integration**: Uses free third-party APIs for product data lookup
- 📱 **Cross-Platform**: Works on iOS, Android, and Web
- ⚡ **TypeScript**: Fully typed for better development experience

## Get started

### Clone the Repository

First, clone the repository from GitHub:

```bash
git clone https://github.com/nh0xThi/Beauty-Scan.git
cd Beauty-Scan
```

Or if you prefer using SSH:

```bash
git clone git@github.com:nh0xThi/Beauty-Scan.git
cd Beauty-Scan
```

### Prerequisites

- Node.js (v18 or later)
- npm or yarn
- Git (for cloning the repository)
- For camera functionality, you'll need a **development build** (camera doesn't work in Expo Go)

### Installation

1. Install dependencies:

```bash
npm install
```

2. Start the development server:

```bash
npm run start
```

### Running the App

**Important**: The camera feature requires a development build. Expo Go does not support native camera modules.

#### Option 1: Development Build (Recommended)

Create a development build to test camera functionality:

```bash
npm run development-builds
```

Or manually:

```bash
# For iOS
npx eas build --profile development --platform ios

# For Android
npx eas build --profile development --platform android
```

#### Option 2: Web Development (Webcam Support)

The app supports webcam access on web browsers:

```bash
npm run web
```

Or:

```bash
npm run start
# Then press 'w' to open in web browser
```

**Web Features**:
- ✅ Webcam access for barcode scanning
- ✅ Works in modern browsers (Chrome, Firefox, Safari, Edge)
- ✅ Automatic camera permission requests
- ✅ Uses front-facing webcam by default

**Note**: Make sure to allow camera permissions when prompted by your browser.

#### Option 3: Local Development (Mobile)

For local development on mobile devices:

```bash
npm run start
```

Then choose:
- [an Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [an iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go) (limited - camera won't work)

### Using the App

1. **Home Screen**: Tap the "📷 Scan Product" button
2. **Scan Screen**: Point your camera at a product barcode
3. **Product Details**: View comprehensive product information
4. **Scan Again**: Tap "Scan Another Product" to continue scanning

## Testing the App

### Prerequisites for Testing

Before testing, ensure you have:
- ✅ Development build installed on your device/emulator (camera won't work in Expo Go)
- ✅ Camera permissions granted
- ✅ Internet connection (required for API calls)

### Testing on Physical Device (Recommended)

1. **Build and Install Development Build**:
   ```bash
   # For iOS
   npx eas build --profile development --platform ios
   
   # For Android
   npx eas build --profile development --platform android
   ```

2. **Install the build** on your device using the provided link or QR code

3. **Grant Camera Permission**: When you first open the scan screen, grant camera permission

### Testing on Emulator/Simulator

**iOS Simulator**:
- Camera functionality is limited on iOS Simulator
- You can test UI and navigation, but barcode scanning may not work properly
- Use a physical device for full camera testing

**Android Emulator**:
- Camera can be tested using the emulator's virtual camera
- Go to Extended Controls → Camera → Webcam to use your computer's camera
- Or use virtual scene for testing

### Test Scenarios

#### 1. Basic Barcode Scanning Test

**Steps**:
1. Open the app
2. Tap "📷 Scan Product" button
3. Point camera at a beauty product barcode
4. Wait for scan detection
5. Verify product details are displayed

**Expected Result**: 
- Camera opens with scanning frame
- Barcode is detected automatically
- Product information appears on details screen

#### 2. Test with Real Beauty Products

**Recommended Test Barcodes** (USA Beauty Products):
- **Maybelline Mascara**: UPC `079400500100`
- **L'Oreal Foundation**: UPC `360054290200`
- **Neutrogena Face Wash**: UPC `070330500100`
- **Olay Moisturizer**: UPC `079400500100`

**Steps**:
1. Find a beauty product with a visible barcode
2. Ensure good lighting
3. Hold camera steady, 4-6 inches from barcode
4. Wait for automatic detection

**Expected Result**: Product details including name, brand, category, and image

#### 3. Test Error Handling

**Test Case 1: Invalid Barcode**
- Scan a non-product barcode (like a QR code)
- **Expected**: Error message or "Product not found"

**Test Case 2: Product Not in Database**
- Scan a barcode that doesn't exist in the API database
- **Expected**: "Product not found" message with option to scan again

**Test Case 3: Poor Lighting**
- Try scanning in low light
- **Expected**: App should still attempt to scan, may take longer

#### 4. Test UI and Navigation

**Test Scenarios**:
1. **Home Screen**:
   - Verify "Scan Product" button is visible and clickable
   - Check baby pink theme colors
   - Verify instructions are displayed

2. **Scan Screen**:
   - Verify camera view appears
   - Check scanning frame (pink corners) is visible
   - Test "Scan Again" button after scanning
   - Test "Cancel" button to go back

3. **Product Details Screen**:
   - Verify all product information displays correctly
   - Check product image loads (if available)
   - Test "Scan Another Product" button
   - Test "Back" button navigation

#### 5. Test API Integration

**Test API Responses**:
1. **Successful Lookup**: Scan a known product
   - Verify data is fetched and displayed correctly
   - Check all fields populate (name, brand, category, etc.)

2. **API Fallback**: 
   - If primary API fails, verify fallback API is used
   - Check console logs for API errors

3. **Network Issues**:
   - Disable internet connection
   - Try scanning
   - **Expected**: Error message about network/API failure

### Testing Without Physical Barcodes

If you don't have physical products to test with:

1. **Use Barcode Generator**:
   - Generate test barcodes online
   - Display on another device/computer screen
   - Scan from screen (may work depending on screen quality)

2. **Test with Barcode Images**:
   - Find barcode images online
   - Display on a screen
   - Scan from the screen

3. **Mock API Responses** (Development):
   - Temporarily modify `services/barcode-api.ts`
   - Return mock product data for testing UI

### Quick Test Checklist

- [ ] App launches without errors
- [ ] Home screen displays correctly with baby pink theme
- [ ] "Scan Product" button navigates to scan screen
- [ ] Camera permission is requested and granted
- [ ] Camera view displays correctly
- [ ] Scanning frame (pink corners) is visible
- [ ] Barcode can be scanned successfully
- [ ] Product details screen displays after scan
- [ ] Product information is accurate and complete
- [ ] "Scan Again" button works
- [ ] "Back" button navigates correctly
- [ ] Error handling works for invalid/not found products
- [ ] App handles network errors gracefully

### Debugging Tips

1. **Check Console Logs**:
   ```bash
   npx expo start
   # Watch the terminal for API errors and debugging info
   ```

2. **Enable Debug Mode**:
   - Shake device or press `Cmd+D` (iOS) / `Cmd+M` (Android)
   - Open React Native Debugger
   - Check Network tab for API calls

3. **Test API Directly**:
   ```bash
   # Test UPC Item DB API
   curl "https://api.upcitemdb.com/prod/trial/lookup?upc=079400500100"
   
   # Test Open Beauty Facts API
   curl "https://world.openbeautyfacts.org/api/v0/product/079400500100.json"
   ```

4. **Clear Cache**:
   ```bash
   npx expo start --clear
   ```

### Performance Testing

- **Scan Speed**: Test how quickly barcodes are detected
- **API Response Time**: Measure time from scan to product display
- **Image Loading**: Verify product images load efficiently
- **Memory Usage**: Check for memory leaks during multiple scans

## Project Structure

```
app/
├── (tabs)/
│   ├── index.tsx          # Home screen with scan button
│   └── _layout.tsx        # Tab navigation layout
├── scan.tsx               # Barcode scanner screen
├── product-details.tsx    # Product information display
└── _layout.tsx            # Root layout

services/
└── barcode-api.ts         # API service for product lookup

constants/
└── theme.ts               # Baby pink theme colors
```

## API Integration

The app uses free third-party APIs optimized for beauty products:

- **Primary**: UPC Item DB API (free tier, 100 requests/day) - Excellent coverage for USA beauty and cosmetics products
- **Fallback**: Open Beauty Facts API (free, no API key) - Specialized database for beauty and personal care products

Both APIs are real, working services that provide accurate product information including:
- Product names and brands
- Categories (beauty, cosmetics, skincare, etc.)
- Product images
- Ingredients lists
- Size/volume information
- Pricing data

You can modify the API service in `services/barcode-api.ts` to use different providers if needed.

## Technology Stack

- **Framework**: Expo SDK 54
- **Language**: TypeScript
- **Navigation**: Expo Router (file-based routing)
- **Camera**: expo-camera
- **UI**: React Native with custom themed components
- **Image Handling**: expo-image

## Workflows

This project is configured to use [EAS Workflows](https://docs.expo.dev/eas/workflows/get-started/) to automate some development and release processes. These commands are set up in [`package.json`](./package.json) and can be run using NPM scripts in your terminal.

### Previews

Run `npm run draft` to [publish a preview update](https://docs.expo.dev/eas/workflows/examples/publish-preview-update/) of your project, which can be viewed in Expo Go or in a development build.

### Development Builds

Run `npm run development-builds` to [create a development build](https://docs.expo.dev/eas/workflows/examples/create-development-builds/). Note - you'll need to follow the [Prerequisites](https://docs.expo.dev/eas/workflows/examples/create-development-builds/#prerequisites) to ensure you have the correct emulator setup on your machine.

### Production Deployments

Run `npm run deploy` to [deploy to production](https://docs.expo.dev/eas/workflows/examples/deploy-to-production/). Note - you'll need to follow the [Prerequisites](https://docs.expo.dev/eas/workflows/examples/deploy-to-production/#prerequisites) to ensure you're set up to submit to the Apple and Google stores.

## Hosting

Expo offers hosting for websites and API functions via EAS Hosting. See the [Getting Started](https://docs.expo.dev/eas/hosting/get-started/) guide to learn more.


## Development

### Code Style

- **TypeScript**: All code is written in TypeScript with strict type checking
- **Theming**: Uses a baby pink color scheme defined in `constants/theme.ts`
- **Components**: Reusable themed components in `components/` directory

### Adding Features

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

### Linting

Run the linter to check for code issues:

```bash
npm run lint
```

## Troubleshooting

### Camera Not Working

If the camera doesn't work, make sure you're using a **development build**, not Expo Go. Camera permissions are automatically requested when you first open the scan screen.

### Product Not Found

If a product isn't found after scanning:
- The barcode might not be in the database
- Try scanning again with better lighting
- Ensure the barcode is clearly visible and not damaged

### Build Issues

If you encounter build errors:
- Clear cache: `npx expo start --clear`
- Reinstall dependencies: `rm -rf node_modules && npm install`
- Check Expo SDK version compatibility

## Repository

This project is available on GitHub:

🔗 **GitHub Repository**: [https://github.com/nh0xThi/Beauty-Scan](https://github.com/nh0xThi/Beauty-Scan)

### Quick Start from GitHub

To get started with this project, clone it from GitHub:

```bash
# Clone the repository
git clone https://github.com/nh0xThi/Beauty-Scan.git

# Navigate to the project directory
cd Beauty-Scan

# Install dependencies
npm install

# Start the development server
npm run start
```

### Contributing

Contributions are welcome! If you'd like to contribute to this project:

1. Fork the repository on GitHub
2. Clone your fork locally: `git clone https://github.com/YOUR_USERNAME/Beauty-Scan.git`
3. Create a feature branch: `git checkout -b feature/amazing-feature`
4. Make your changes and commit them: `git commit -m 'Add some amazing feature'`
5. Push to your fork: `git push origin feature/amazing-feature`
6. Open a Pull Request on the original repository

### License

This project is open source and available for use.


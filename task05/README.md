# Task: BMI Calculator Flutter Application

## 📱 Project Description
Create a fully functional BMI (Body Mass Index) Calculator mobile application using Flutter with a modern, user-friendly interface.

## 🎯 Learning Objectives
- Implement interactive UI components (sliders, counters)
- Handle user input and state management
- Perform mathematical calculations
- Create responsive and visually appealing layouts
- Understand form validation and user feedback

## 📋 Application Requirements

### 1. Core Features
- **Gender Selection**: Male/Female toggle
- **Height Adjustment**: Slider with visual feedback
- **Weight Selection**: Increment/Decrement counter
- **Age Selection**: Increment/Decrement counter
- **BMI Calculation**: Automatic calculation with display
- **Result Interpretation**: BMI category classification

### 2. UI Layout Structure

```
┌─────────────────────────────────┐
│        BMI CALCULATOR           │ ← AppBar
├─────────────────────────────────┤
│                                 │
│  ┌───────┐    ┌───────┐        │
│  │   ♂   │    │   ♀   │        │ ← Gender Selection
│  │ Male  │    │Female │        │
│  └───────┘    └───────┘        │
│                                 │
│      HEIGHT (cm)                │
│          [ 180 ]                │ ← Height Display
│  ────[════════════════]─────   │ ← Slider (120-220 cm)
│                                 │
│  ┌──────────┐  ┌──────────┐    │
│  │  WEIGHT  │  │   AGE    │    │
│  │    75    │  │    25    │    │ ← Weight & Age Display
│  │  ─   +   │  │  ─   +   │    │ ← Counter Controls
│  └──────────┘  └──────────┘    │
│                                 │
│  ┌─────────────────────────┐   │
│  │     CALCULATE BMI       │   │ ← Calculate Button
│  └─────────────────────────┘   │
│                                 │
│                                 │
│  (Results appear here after     │
│   calculation)                  │
│                                 │
└─────────────────────────────────┘
```

### 3. Detailed Component Specifications

#### A. Gender Selection
- **Layout**: Two equal-sized cards side by side
- **Male Card**:
  - Icon: ♂ (Male symbol)
  - Text: "MALE"
  - Color: Active state - blue, Inactive state - grey
- **Female Card**:
  - Icon: ♀ (Female symbol)
  - Text: "FEMALE"
  - Color: Active state - pink, Inactive state - grey
- **Behavior**: Only one gender can be selected at a time

#### B. Height Selection
- **Label**: "HEIGHT"
- **Current Value Display**: Large centered number with "cm" unit
- **Slider**:
  - Range: 120 cm to 220 cm
  - Default: 180 cm
  - Thumb color: Primary accent color
  - Active track color: Primary color
  - Inactive track color: Grey
- **Min/Max Indicators**: "120" on left, "220" on right

#### C. Weight Counter
- **Label**: "WEIGHT"
- **Current Value**: Displayed in large font
- **Unit**: "kg" displayed below value
- **Controls**:
  - Minus button (left): Decreases by 1 kg
  - Plus button (right): Increases by 1 kg
- **Range**: 30 kg to 200 kg

#### D. Age Counter
- **Label**: "AGE"
- **Current Value**: Displayed in large font
- **Unit**: "yrs" displayed below value
- **Controls**:
  - Minus button (left): Decreases by 1 year
  - Plus button (right): Increases by 1 year
- **Range**: 10 years to 100 years

#### E. Calculate Button
- **Text**: "CALCULATE BMI"
- **Style**: Rounded rectangle, full width
- **Color**: Primary accent color
- **Text Color**: White
- **Behavior**: On press, calculate and display BMI results

### 4. BMI Calculation Logic
```dart
// Formula: BMI = weight (kg) / (height (m) * height (m))
double calculateBMI(double heightCm, double weightKg) {
  double heightM = heightCm / 100;
  return weightKg / (heightM * heightM);
}
```

### 5. BMI Categories
| BMI Range      | Category      | Color Code |
|----------------|---------------|------------|
| Below 18.5     | Underweight   | Blue       |
| 18.5 - 24.9    | Normal        | Green      |
| 25.0 - 29.9    | Overweight    | Yellow     |
| 30.0 and above | Obese         | Red        |

### 6. Results Display
After calculation, show:
- **BMI Value**: Rounded to 1 decimal place
- **Category**: With corresponding color
- **Interpretation**: Short health message
- **Range Information**: Ideal BMI range

### 7. Color Scheme
- **Primary**: `Colors.blueAccent[700]`
- **Secondary**: `Colors.pinkAccent[400]`
- **Background**: `Colors.grey[900]` (Dark theme) or `Colors.white` (Light theme)
- **Text**: `Colors.white` (Dark) or `Colors.black` (Light)
- **Cards**: `Colors.blueGrey[800]` (Dark) or `Colors.grey[100]` (Light)

## 🛠️ Implementation Guidelines

### 1. State Management
- Use `StatefulWidget` for the main screen
- Track variables: `gender`, `height`, `weight`, `age`, `bmiResult`

### 2. Widget Structure
```dart
Column(
  children: [
    // Gender Selection Row
    Row(children: [MaleCard(), FemaleCard()]),
    
    SizedBox(height: 20),
    
    // Height Section
    HeightSlider(),
    
    SizedBox(height: 20),
    
    // Weight and Age Row
    Row(children: [WeightCounter(), AgeCounter()]),
    
    SizedBox(height: 30),
    
    // Calculate Button
    CalculateButton(),
    
    SizedBox(height: 20),
    
    // Results Section (conditionally visible)
    ResultsDisplay(),
  ],
)
```

### 3. Interactive Components
- **Slider**: Use `Slider` widget with `onChanged` callback
- **Counters**: Use `IconButton` with increment/decrement logic
- **Gender Cards**: Use `GestureDetector` or `InkWell` for tap interaction

### 4. Responsive Design
- Use `MediaQuery` for screen dimensions
- Appropriate spacing with `SizedBox`
- Flexible and Expanded widgets for proportional layouts

## ✅ Acceptance Criteria

### Functional Requirements
- [ ] Gender selection works (mutually exclusive)
- [ ] Height slider updates value in real-time
- [ ] Weight counter increments/decrements properly
- [ ] Age counter increments/decrements properly
- [ ] Calculate button triggers BMI calculation
- [ ] BMI is calculated correctly using the formula
- [ ] Results show BMI value and category
- [ ] Category is color-coded appropriately
- [ ] All values have reasonable limits
- [ ] App handles edge cases (min/max values)

### UI Requirements
- [ ] Clean, modern interface
- [ ] Consistent spacing and alignment
- [ ] Readable text sizes
- [ ] Intuitive controls
- [ ] Visual feedback for interactions
- [ ] Results displayed clearly

### Code Requirements
- [ ] Well-structured widget tree
- [ ] Proper state management
- [ ] Comments for complex logic
- [ ] Error-free compilation
- [ ] No console errors/warnings
- [ ] Responsive layout

## 🚀 Bonus Features

1. **Theme Toggle**: Switch between light/dark mode
2. **Unit Conversion**: Toggle between kg/lb and cm/feet
3. **History**: Save previous calculations
4. **Detailed Analysis**: Show health recommendations
5. **Share Results**: Export BMI results
6. **Animations**: Smooth transitions between states
7. **Sound/Vibration**: Haptic feedback on interactions
8. **Personalized Tips**: Gender/age specific advice

## 📱 Expected Output Examples

### Input Example:
```
Gender: Male
Height: 175 cm
Weight: 70 kg
Age: 25 years
```

### Output Example:
```
Your BMI Result

22.9

Normal Weight

You have a normal body weight.
Good job!

Healthy BMI range: 18.5 - 24.9
```

## 🗂️ File Structure
```
lib/
├── main.dart
├── screens/
│   └── bmi_calculator.dart
├── widgets/
│   ├── gender_card.dart
│   ├── height_slider.dart
│   ├── counter_widget.dart
│   └── result_card.dart
└── utils/
    └── bmi_calculator.dart
```

## ⏱️ Estimated Development Time
- **Beginner**: 8-12 hours
- **Intermediate**: 4-6 hours
- **Advanced**: 2-3 hours

## 📚 Learning Outcomes
By completing this project, you will master:
- State management in Flutter
- Interactive UI components
- Mathematical calculations in Dart
- Responsive layout design
- User input validation
- Conditional rendering
- Theming and styling
- Event handling

This BMI Calculator application provides comprehensive practice with essential Flutter development concepts while creating a practical, real-world application.
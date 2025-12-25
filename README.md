# Ex09 Event Registration Web Application
# Date:
# AIM:
To design, develop and deploy a web application for event registration.

# DESIGN STEPS:
## Step 1:
Create a new frame.

## Step 2:
Select any one preset size of your choice.

## Step 3:
Select the shapes you need.

## Step 4:
Import images as needed.

## Step 5:
Create pages based on your need and link them.

## Step 6:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# DESIGN TOOL:
Figma

# CODE:
Welcome Page
```
import { Button } from "./ui/button";
import { Calendar } from "lucide-react";
import logo from "figma:asset/6ffed03c6350543c5c176909e45ea437ad796750.png";

interface WelcomePageProps {
  onNext: () => void;
}

export function WelcomePage({ onNext }: WelcomePageProps) {
  return (
    <div className="flex flex-col items-center justify-center text-center px-4 py-12">
      <div className="mb-8">
        <img src={logo} alt="Saveetha Engineering College" className="h-16 w-auto" />
      </div>
      
      <div className="inline-flex items-center justify-center w-20 h-20 rounded-full bg-gradient-to-br from-purple-100 to-pink-100 mb-6">
        <Calendar className="w-10 h-10 text-purple-600" />
      </div>
      
      <h1 className="mb-4 text-transparent bg-clip-text bg-gradient-to-r from-blue-600 to-purple-600">Join Our Event</h1>
      <p className="text-gray-700 mb-8 max-w-md">
        We're excited to have you join us for an amazing experience. Register now to secure your spot!
      </p>
      
      <Button onClick={onNext} size="lg" className="px-8 bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-700 hover:to-purple-700">
        Register Now
      </Button>
    </div>
  );
}
```
Registration Form
```
import { useState } from "react";
import { Button } from "./ui/button";
import { Input } from "./ui/input";
import { Label } from "./ui/label";
import { ArrowLeft } from "lucide-react";
import logo from "figma:asset/6ffed03c6350543c5c176909e45ea437ad796750.png";

interface RegistrationFormProps {
  onNext: (data: FormData) => void;
  onBack: () => void;
}

export interface FormData {
  firstName: string;
  lastName: string;
  email: string;
  phone: string;
}

export function RegistrationForm({ onNext, onBack }: RegistrationFormProps) {
  const [formData, setFormData] = useState<FormData>({
    firstName: "",
    lastName: "",
    email: "",
    phone: "",
  });

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    onNext(formData);
  };

  const handleChange = (field: keyof FormData, value: string) => {
    setFormData((prev) => ({ ...prev, [field]: value }));
  };

  return (
    <div className="w-full max-w-md px-4 py-8">
      <div className="flex items-center justify-center mb-6">
        <img src={logo} alt="Saveetha Engineering College" className="h-14 w-auto" />
      </div>
      
      <button
        onClick={onBack}
        className="flex items-center gap-2 text-purple-600 hover:text-purple-700 mb-6"
      >
        <ArrowLeft className="w-4 h-4" />
        Back
      </button>

      <div className="mb-8">
        <h2 className="mb-2 text-transparent bg-clip-text bg-gradient-to-r from-blue-600 to-purple-600">Registration Details</h2>
        <p className="text-gray-600">Please fill in your information to complete your registration.</p>
      </div>

      <form onSubmit={handleSubmit} className="space-y-6">
        <div className="space-y-2">
          <Label htmlFor="firstName" className="text-gray-700">First Name</Label>
          <Input
            id="firstName"
            type="text"
            placeholder="Enter your first name"
            value={formData.firstName}
            onChange={(e) => handleChange("firstName", e.target.value)}
            className="border-purple-200 focus:border-purple-500 focus:ring-purple-500"
            required
          />
        </div>

        <div className="space-y-2">
          <Label htmlFor="lastName" className="text-gray-700">Last Name</Label>
          <Input
            id="lastName"
            type="text"
            placeholder="Enter your last name"
            value={formData.lastName}
            onChange={(e) => handleChange("lastName", e.target.value)}
            className="border-purple-200 focus:border-purple-500 focus:ring-purple-500"
            required
          />
        </div>

        <div className="space-y-2">
          <Label htmlFor="email" className="text-gray-700">Email</Label>
          <Input
            id="email"
            type="email"
            placeholder="your.email@example.com"
            value={formData.email}
            onChange={(e) => handleChange("email", e.target.value)}
            className="border-purple-200 focus:border-purple-500 focus:ring-purple-500"
            required
          />
        </div>

        <div className="space-y-2">
          <Label htmlFor="phone" className="text-gray-700">Phone Number</Label>
          <Input
            id="phone"
            type="tel"
            placeholder="+1 (555) 000-0000"
            value={formData.phone}
            onChange={(e) => handleChange("phone", e.target.value)}
            className="border-purple-200 focus:border-purple-500 focus:ring-purple-500"
            required
          />
        </div>

        <Button type="submit" className="w-full bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-700 hover:to-purple-700" size="lg">
          Complete Registration
        </Button>
      </form>
    </div>
  );
}
```
Thank you
```
import { Button } from "./ui/button";
import { CheckCircle } from "lucide-react";
import { FormData } from "./RegistrationForm";
import logo from "figma:asset/6ffed03c6350543c5c176909e45ea437ad796750.png";

interface ThankYouPageProps {
  userData: FormData;
  onReset: () => void;
}

export function ThankYouPage({ userData, onReset }: ThankYouPageProps) {
  return (
    <div className="flex flex-col items-center justify-center text-center px-4 py-12">
      <div className="mb-8">
        <img src={logo} alt="Saveetha Engineering College" className="h-16 w-auto" />
      </div>
      
      <div className="inline-flex items-center justify-center w-20 h-20 rounded-full bg-gradient-to-br from-green-100 to-emerald-100 mb-6">
        <CheckCircle className="w-10 h-10 text-green-600" />
      </div>
      
      <h1 className="mb-4 text-transparent bg-clip-text bg-gradient-to-r from-green-600 to-emerald-600">Thank You for Registering!</h1>
      <p className="text-gray-700 mb-8 max-w-md">
        We've received your registration, {userData.firstName}. A confirmation email has been sent to{" "}
        <span className="text-gray-900">{userData.email}</span>.
      </p>

      <div className="bg-gradient-to-br from-purple-50 to-pink-50 rounded-lg p-6 mb-8 max-w-md w-full border border-purple-100">
        <h3 className="text-sm text-purple-700 mb-4">Registration Summary</h3>
        <div className="space-y-3 text-left">
          <div>
            <p className="text-sm text-purple-600">Name</p>
            <p className="text-gray-900">{userData.firstName} {userData.lastName}</p>
          </div>
          <div>
            <p className="text-sm text-purple-600">Email</p>
            <p className="text-gray-900">{userData.email}</p>
          </div>
          <div>
            <p className="text-sm text-purple-600">Phone</p>
            <p className="text-gray-900">{userData.phone}</p>
          </div>
        </div>
      </div>

      <Button onClick={onReset} variant="outline" className="border-purple-300 text-purple-700 hover:bg-purple-50">
        Register Another Person
      </Button>
    </div>
  );
}
```
# OUTPUT:
<img width="1918" height="1075" alt="image" src="https://github.com/user-attachments/assets/60a69f9c-2fdf-4f89-a973-c5671c8bdadc" />




# RESULT:
The program to design, develop and deploy a web application for event registration is completed successfully.

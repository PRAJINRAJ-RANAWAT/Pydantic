# 🚀 Pydantic Basics — Models & Validation

A beginner-friendly guide to understanding and using Pydantic for data validation in Python.

This repo walks through everything from simple dataclasses to powerful Pydantic models with validation, constraints, and nested structures.

---

## 📌 What You’ll Learn

* Difference between `dataclass` vs Pydantic
* Creating models using `BaseModel`
* Type validation & error handling
* Optional fields & defaults
* Lists & type casting
* Nested models (real-world structures)
* Field constraints using `Field`
* Best practices like `default_factory`

---

## 🧠 Why Pydantic?

Python normally **does NOT enforce types at runtime**.

```python
age: int = "19"  # This works 😬
```

Pydantic fixes that:

```python
age: int = "Delhi"  # ❌ Throws ValidationError
```

👉 It ensures:

* Correct types
* Clean data
* Safe APIs
* Reliable pipelines

---

## ⚙️ Installation

```bash
pip install pydantic
```

---

## 🏗️ Project Structure

```
pydantic-basics/
│
├── basics.ipynb   # Full walkthrough notebook
├── README.md      # You are here 😎
```

---

## 🔥 Core Concepts

### 1. Dataclass vs Pydantic

```python
@dataclass
class Person:
    name: str
    age: int
```

⚠️ Dataclass does NOT validate types.

---

```python
class Person(BaseModel):
    name: str
    age: int
```

✅ Pydantic enforces validation.

---

### 2. Validation Errors

```python
Person(age="Delhi")  
# ❌ Raises ValidationError
```

---

### 3. Optional Fields

```python
class Employee(BaseModel):
    salary: Optional[float] = None
    isActive: Optional[bool] = True
```

✔ Optional + Default = Not required

---

### 4. Lists & Type Casting

```python
class Classroom(BaseModel):
    students: List[str]
```

```python
students=("Alice", "Bob")  # tuple
```

👉 Automatically converted to list ✅

---

### 5. Nested Models

```python
class Address(BaseModel):
    city: str

class Customer(BaseModel):
    address: Address
```

```python
Customer(address={"city": "Ahmedabad"})
```

🔥 Clean structured data

---

### 6. Field Constraints

```python
class Item(BaseModel):
    price: float = Field(gt=0, lt=10000)
```

✔ Prevent invalid values
✔ Built-in validation rules

---

### 7. default_factory (Important ⚠️)

```python
email: str = Field(default_factory=lambda: "user@example.com")
```

💡 Prevents shared mutable defaults

---

## 🧪 Error Handling

```python
try:
    Classroom(students=["Praju", 35])
except Exception as e:
    print(e)
```

✔ Always wrap risky validation

---

## 🎯 Use Cases

* API validation (FastAPI 🔥)
* Data pipelines
* Config management
* ML input validation
* Backend systems

---

## 💡 Key Takeaways

* Python types ≠ enforced
* Pydantic = runtime validation
* Cleaner, safer, production-ready code

---

## 👨‍💻 Author

**Prajinraj Bhavesh Ranawat**

---

## ⭐ Bonus

If you're building something like:

* AI agents
* DevOps tools (👀 VibeOps)
* APIs

👉 Pydantic is **non-negotiable**

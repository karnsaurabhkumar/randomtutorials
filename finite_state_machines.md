**Finite State Machine (FSM)**

A Finite State Machine (FSM) is a mathematical model of computation that provides a way to design and describe the behavior of a system with a finite number of states, transitions between these states, and actions. FSMs are used in many areas, such as digital circuit design, computer programming, and linguistics.

There are two main types of FSM:
1. **Determinate Finite Automata (DFA)**: Accepts or rejects a string of symbols.
2. **Mealy and Moore Machines**: Produces an output value for each input value.

**Key Elements of FSM**:
1. **States**: Distinct conditions in which an FSM can exist.
2. **Transitions**: The rules for moving from one state to another.
3. **Input**: Events or conditions that can trigger a transition.
4. **Output** (for Mealy and Moore machines): The response of the machine based on the current state and input.

---

**Example: Simple Turnstile FSM**

Consider a turnstile used in a metro station. It has two states:
1. Locked
2. Unlocked

**States**:
- Locked
- Unlocked

**Transitions**:
- When in the "Locked" state, inserting a coin changes the state to "Unlocked".
- When in the "Unlocked" state, passing through the turnstile changes the state back to "Locked".

**FSM Diagram**:
```
       coin
  +---------+          +-----------+
  |  Locked +--------->| Unlocked  |
  +----+----+          +-----+-----+
       ^                     |
       |                     |
       +--------+            |
                pass         |
                through      |
                <------------+
```

---

**Trying it on Mac OS**:

1. **Install Python**:
   - Most Macs come with Python pre-installed. You can check the installed version with `python3 --version`.
   - If not installed, download and install Python from the official website.

2. **Install Graphviz** (to visualize the FSM):
   - Using Homebrew: `brew install graphviz`

3. **Create and run the FSM**:
   - We will use the `transitions` library in Python to create an FSM.
   - First, install the library: `pip3 install transitions`

4. **Python Code**:

```python
from transitions import Machine

class Turnstile:
    pass

turnstile = Turnstile()

states = ['locked', 'unlocked']
transitions = [
    {'trigger': 'coin', 'source': 'locked', 'dest': 'unlocked'},
    {'trigger': 'pass_through', 'source': 'unlocked', 'dest': 'locked'}
]

machine = Machine(model=turnstile, states=states, transitions=transitions, initial='locked')

# Test
turnstile.coin()  # Should change state to unlocked
print(turnstile.state)  # Expected output: unlocked

turnstile.pass_through()  # Should change state to locked
print(turnstile.state)  # Expected output: locked
```

5. **Run the Code**:
   - Save the code to a file, say `turnstile_fsm.py`.
   - Run it using: `python3 turnstile_fsm.py`

6. **Visualize the FSM**:
   - Using the `transitions` library, you can also generate a Graphviz diagram for visualization.
   - Update the code to add `machine.get_graph().draw('turnstile_fsm.png', prog='dot')` before the test section.
   - Run the code again to generate the FSM diagram. You can open the `turnstile_fsm.png` file to view the FSM diagram.

I hope this tutorial gives you a basic understanding of Finite State Machines and how to implement and visualize them on Mac OS!

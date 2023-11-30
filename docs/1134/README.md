# Conversational AI - End-to-end production-grade chatbot

* Training a production-ready chatbot for a scaffold hire company involves several steps, including data collection, intent classification, entity recognition, dialogue management, and deploying the bot on a platform. I can guide you through the process and provide an example using Python and a framework like Rasa.

* Rasa is an open-source framework for ***building conversational AI***. It allows you to create chatbots with natural language understanding and dialogue management capabilities. For this example, let's assume you have Rasa installed:

1. **Setting Up Rasa:**
   Install Rasa by following the installation guide in their documentation.

2. **Create a Rasa Project:**
   Use the Rasa CLI to create a new project:

   ```bash
   rasa init --no-prompt
   ```

3. **Data Collection:**
   Gather conversations or create sample conversations between users and a scaffold hire company representative. These conversations will serve as training data. Organize them into intents (what the user wants) and entities (specific information in user messages).

4. **Define Intents and Entities:**
   In Rasa, define intents (such as asking for scaffold types, pricing, safety precautions) and entities (e.g., scaffold types, rental durations) based on your collected data.

5. **Train the Model:**
   Use the Rasa training data to train the chatbot model:

   ```bash
   rasa train
   ```

6. **Dialogue Management:**
   Create a dialogue management system using Rasa's stories and rules to handle different conversation paths and guide users through scaffold hiring processes or FAQs.

7. **Integration and Deployment:**
   Integrate the trained model with your preferred platform or deploy it using Rasa's server or a cloud service.

Here's a simplified example of how you'd structure intents, entities, and responses in Rasa's training data format (`data/nlu.yml` and `data/stories.yml`):

**nlu.yml**
```yaml
version: "2.0"

nlu:
- intent: ask_scaffold_types
  examples: |
    - What types of scaffolds do you offer?
    - Can you tell me about your scaffold types?
    - Kind of scaffolds available?

- intent: ask_rental_prices
  examples: |
    - How much does it cost to rent a scaffold?
    - What's the rental price?
    - Price to rent a scaffold for a week?

# Add more intents for safety precautions, booking, etc.

```

**stories.yml**
```yaml
version: "2.0"

stories:
- story: scaffold types inquiry
  steps:
  - intent: ask_scaffold_types
  - action: respond_scaffold_types

- story: rental prices inquiry
  steps:
  - intent: ask_rental_prices
  - action: respond_rental_prices

# Add more stories for different conversation flows
```

**actions.py**
```python
from typing import Any, Text, Dict, List
from rasa_sdk import Action, Tracker
from rasa_sdk.executor import CollectingDispatcher

class ActionRespondScaffoldTypes(Action):
    def name(self) -> Text:
        return "respond_scaffold_types"

    def run(self, dispatcher: CollectingDispatcher,
            tracker: Tracker,
            domain: Dict[Text, Any]) -> List[Dict[Text, Any]]:
        response = "We offer various scaffold types including suspended, supported, mobile, and aerial work platforms."
        dispatcher.utter_message(text=response)
        return []

# Implement similar actions for other intents like rental prices, safety precautions, etc.
```

*This example is a basic structure; a real production chatbot would involve more extensive training data, more sophisticated dialogue management, integration with backend systems, and continuous improvement based on user interactions and feedback.*

*For a complete end-to-end production-grade chatbot, it's crucial to iterate, test extensively, and continuously improve based on user interactions and feedback.*

---

Documentation By: **Raymond C. TURNER**

**Revision:** Thursday 30th November 2023
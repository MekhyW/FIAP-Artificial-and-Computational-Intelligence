```python
#CODE IS DEPRECATED; WATSON IS NO LONGER INTERACTED WITH LIKE THIS
```


```python
import json
from watson_developer_cloud import NaturalLanguageUnderstandingV1 
from watson_developer_cloud.natural_language_understanding_v1 import Features, ConceptsOptions, RelationsOptions, EmotionOptions, EntitiesOptions, SemanticRolesOptions, SentimentOptions
```


```python
natural_language_understanding = NaturalLanguageUnderstandingV1(
  username='coloque_aqui_seu_usuario',
  password='aqui_sua_senha',
  version='2018-03-16')
```

    C:\Users\Felipe Catapano\AppData\Roaming\Python\Python37\site-packages\ipykernel_launcher.py:4: DeprecationWarning: watson-developer-cloud moved to ibm-watson. To get updates, use the new package.
      after removing the cwd from sys.path.
    


```python
response = natural_language_understanding.analyze(
  text='Who is the president of Brazil?',
  features=Features(
    concepts=ConceptsOptions(),
    emotion=EmotionOptions(),
    entities=EntitiesOptions(),
    sentiment=SentimentOptions(),
    ))
```


```python
print(json.dumps(response, indent=2))
```


```python
{
  "emotion": {
    "document": {
      "emotion": {
        "anger": 0.149442, 
        "joy": 0.151672, 
        "sadness": 0.117418, 
        "fear": 0.047087, 
        "disgust": 0.198362
      }
    }
  }, 
  "sentiment": {
    "document": {
      "score": 0.0, 
      "label": "neutral"
    }
  }, 
  "language": "en", 
  "entities": [
    {
      "relevance": 0.33, 
      "text": "president", 
      "type": "JobTitle", 
      "count": 1
    }, 
    {
      "relevance": 0.33, 
      "text": "Brazil", 
      "disambiguation": {
        "subtype": [
          "GovernmentalJurisdiction", 
          "CompanyShareholder", 
          "Country"
        ], 
        "name": "Brazil", 
        "dbpedia_resource": "http://dbpedia.org/resource/Brazil"
      }, 
      "type": "Location", 
      "count": 1
    }
  ], 
  "concepts": [
    {
      "relevance": 0.886784, 
      "text": "President", 
      "dbpedia_resource": "http://dbpedia.org/resource/President"
    }, 
    {
      "relevance": 0.862208, 
      "text": "President of the United States", 
      "dbpedia_resource": "http://dbpedia.org/resource/President_of_the_United_States"
    }, 
    {
      "relevance": 0.845824, 
      "text": "Politics of Brazil", 
      "dbpedia_resource": "http://dbpedia.org/resource/Politics_of_Brazil"
    }
  ], 
  "usage": {
    "text_characters": 31, 
    "features": 5, 
    "text_units": 1
  }
}
```


```python
response = natural_language_understanding.analyze(
  text='Steve Jobs is the founder of Apple',
  features=Features(
    entities=EntitiesOptions(),
    semantic_roles=SemanticRolesOptions(),
    ))

print(json.dumps(response, indent=2))
```


```python
{
  "usage": {
    "text_characters": 34, 
    "features": 2, 
    "text_units": 1
  }, 
  "semantic_roles": [
    {
      "action": {
        "text": "is", 
        "verb": {
          "text": "be", 
          "tense": "present"
        }, 
        "normalized": "be"
      }, 
      "sentence": "Steve Jobs is the founder of Apple", 
      "object": {
        "text": "the founder of Apple"
      }, 
      "subject": {
        "text": "Steve Jobs"
      }
    }
  ], 
  "language": "en", 
  "entities": [
    {
      "relevance": 0.33, 
      "text": "Steve Jobs", 
      "disambiguation": {
        "subtype": [
          "BoardMember", 
          "CompanyFounder", 
          "ComputerDesigner", 
          "FilmProducer"
        ], 
        "name": "Steve Jobs", 
        "dbpedia_resource": "http://dbpedia.org/resource/Steve_Jobs"
      }, 
      "type": "Person", 
      "count": 1
    }, 
    {
      "relevance": 0.33, 
      "text": "founder", 
      "type": "JobTitle", 
      "count": 1
    }, 
    {
      "relevance": 0.33, 
      "text": "Apple", 
      "type": "Company", 
      "count": 1
    }
  ]
}
```


```python
response = natural_language_understanding.analyze(
  text='Steve Jobs é o fundador da Apple',
  features=Features(
    entities=EntitiesOptions(),
    semantic_roles=SemanticRolesOptions(),
    ))

print(json.dumps(response, indent=2))
```


```python
{
  "usage": {
    "text_characters": 32, 
    "features": 2, 
    "text_units": 1
  }, 
  "semantic_roles": [], 
  "language": "en", 
  "entities": [
    {
      "relevance": 0.33, 
      "text": "Steve Jobs", 
      "disambiguation": {
        "subtype": [
          "BoardMember", 
          "CompanyFounder", 
          "ComputerDesigner", 
          "FilmProducer"
        ], 
        "name": "Steve Jobs", 
        "dbpedia_resource": "http://dbpedia.org/resource/Steve_Jobs"
      }, 
      "type": "Person", 
      "count": 1
    }, 
    {
      "relevance": 0.33, 
      "text": "Apple", 
      "type": "Company", 
      "count": 1
    }
  ]
}
```


```python
response = natural_language_understanding.analyze(
  text='Na FIAP, os alunos são muito dedicados.',
  features=Features(
    relations=RelationsOptions(),
    concepts=ConceptsOptions(),
    emotion=EmotionOptions(),
    entities=EntitiesOptions(),
    semantic_roles=SemanticRolesOptions(),
    sentiment=SentimentOptions(),
    ))

print(json.dumps(response, indent=2))
```


```python
{
  "sentiment": {
    "document": {
      "score": 0.0, 
      "label": "neutral"
    }
  }, 
  "language": "pt", 
  "warnings": [
    "concepts: unsupported text language: pt", 
    "emotion: unsupported text language: pt", 
    "semantic_roles: unsupported text language: pt"
  ], 
  "relations": [], 
  "entities": [], 
  "usage": {
    "text_characters": 39, 
    "features": 3, 
    "text_units": 1
  }
}
```

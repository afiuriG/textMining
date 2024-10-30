#  Dataset
  
#  MultiWOZ version...
Multi-Domain Wizard-of-Oz dataset (MultiWOZ), es una collección de datos completamente etiquetados....a fully-labeled collection of human-human written conversations spanning over multiple domains and topics. At a size of 10k dialogues, it is at least one order of magnitude larger than all previous annotated task-oriented corpora.
There are 3,406 single-domain dialogues that include booking if the domain allows for that and 7,032 multi-domain dialogues consisting of at least 2 up to 5 domains. To enforce reproducibility of results, the corpus was randomly split into a train, test and development set. The test and development sets contain 1k examples each. Even though all dialogues are coherent, some of them were not finished in terms of task description. Therefore, the validation and test sets only contain fully successful dialogues thus enabling a fair comparison of models. There are no dialogues from hospital and police domains in validation and testing sets.
Como definido en el punto de acceso al dataset [multiwozDatas???](https://github.com/budzianowski/multiwoz/blob/master/README.md) asociado a la publicación [multiwozPAper???](https://arxiv.org/pdf/2007.12720) a cada dominio podemos describirlo como se muestra en la siguiente tabla:


| Domain     | Categorical slots       | Non-categorical slots   | Intents    |
| ---------- | :---------------------: | :---------------------: | :--------: |
| Restaurant | pricerange, area, bookday, bookpeople | food, name, booktime, address, phone, postcode, ref | find, book |
| Attraction | area, type              | name, address, entrancefee, openhours, entrancefee, openhours, phone, postcode    | find       |
| Hotel      | pricerange, parking, internet, stars, area, type, bookpeople, bookday, bookstay  | name, address, phone, postcode, ref | find, book |
| Taxi       | -                       | destination, departure, arriveby, leaveat, phone, type | book       |
| Train      | destination, departure, day, bookpeople | arriveby, leaveat, trainid, ref, price, duration | find, book |
| Bus        | day                     | departure, destination, leaveat | find       |
| Hospital   | -                       | department , address, phone, postcode | find       |
| Police     | -                       | name, address, phone, postcode | find       |

Of the 61 slots in the schema, the following 35 slots are tracked in the
dialogue state:

```
{
  "attraction-area",
  "attraction-name",
  "attraction-type",
  "bus-day",
  "bus-departure",
  "bus-destination",
  "bus-leaveat",
  "hospital-department",
  "hotel-area",
  "hotel-bookday",
  "hotel-bookpeople",
  "hotel-bookstay",
  "hotel-internet",
  "hotel-name",
  "hotel-parking",
  "hotel-pricerange",
  "hotel-stars",
  "hotel-type",
  "restaurant-area",
  "restaurant-bookday",
  "restaurant-bookpeople",
  "restaurant-booktime",
  "restaurant-food",
  "restaurant-name",
  "restaurant-pricerange",
  "taxi-arriveby",
  "taxi-departure",
  "taxi-destination",
  "taxi-leaveat",
  "train-arriveby",
  "train-bookpeople",
  "train-day",
  "train-departure",
  "train-destination",
  "train-leaveat"
}
```

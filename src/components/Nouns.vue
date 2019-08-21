<template>
  <div id="nouns">
    <ul id="noun-list">
      <li v-for="noun in nouns">
        <div class="noun-card">
          <img :src="noun.image" class="image" /> 
          <p class="word">{{ noun.word }}, <span class="gender">{{ noun.gender }}</span></p>
          
          <button type="button" class="btn btn-outline-dark" 
                  v-on:click="noun.showDeclension = !noun.showDeclension">
            <span v-if="noun.showDeclension">Hide Declension Table</span>
            <span v-else>Show Declension Table</span>
          </button>
          
          <transition name="fade">
            <div v-show="noun.showDeclension" class="declension-table">
              <table class="table table-bordered">
                <thead>
                  <tr>
                    <th scope="col">Case</th>
                    <th scope="col">Singular</th>
                    <th scope="col">Plural</th>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <td>Nominative</td>
                    <td>{{ noun.declension.nominative.singular }}</td>
                    <td>{{ noun.declension.nominative.plural }}</td>
                  </tr>
                  <tr>
                    <td>Genitive</td>
                    <td>{{ noun.declension.genitive.singular }}</td>
                    <td>{{ noun.declension.genitive.plural }}</td>
                  </tr>
                  <tr>
                    <td>Dative</td>
                    <td>{{ noun.declension.dative.singular }}</td>
                    <td>{{ noun.declension.dative.plural }}</td>
                  </tr>
                  <tr>
                    <td>Accusative</td>
                    <td>{{ noun.declension.accusative.singular }}</td>
                    <td>{{ noun.declension.accusative.plural }}</td>
                  </tr>
                  <tr>
                    <td>Ablative</td>
                    <td>{{ noun.declension.ablative.singular }}</td>
                    <td>{{ noun.declension.ablative.plural }}</td>
                  </tr>
                </tbody>
              </table>
            </div>
          </transition>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import { shuffle } from 'underscore';

export default {

  data() {
    return {
      nouns: [
        {
          word: 'rosa', gender: 'F', showDeclension: false, image: require('../assets/rose.png'),
          declension: {
            nominative: {
              singular: 'rosa',
              plural: 'rosae'
            },
            genitive: {
              singular: 'rosae',
              plural: 'rosārum'
            },
            dative: {
              singular: 'rosae',
              plural: 'rosīs'
            },
            accusative: {
              singular: 'rosam',
              plural: 'rosās'
            },
            ablative: {
              singular: 'rosā',
              plural: 'rosīs'
            }
          }
        },
        {
          word: 'lūna', gender: 'F', showDeclension: false, image: require('../assets/moon.png'),
          declension: {
            nominative: {
              singular: 'lūna',
              plural: 'lūnae'
            },
            genitive: {
              singular: 'lūnae',
              plural: 'lūnārum'
            },
            dative: {
              singular: 'lūnae',
              plural: 'lūnīs'
            },
            accusative: {
              singular: 'lūnam',
              plural: 'lūnās'
            },
            ablative: {
              singular: 'lūnā',
              plural: 'lūnīs'
            }
          }
        },
        {
          word: 'cancer', gender: 'M', showDeclension: false, image: require('../assets/crab.png'),
          declension: {
            nominative: {
              singular: 'cancer',
              plural: 'cancrī'
            },
            genitive: {
              singular: 'cancrī',
              plural: 'cancrōrum'
            },
            dative: {
              singular: 'cancrō',
              plural: 'cancrīs'
            },
            accusative: {
              singular: 'cancrum',
              plural: 'cancrōs'
            },
            ablative: {
              singular: 'cancrō',
              plural: 'cancrīs'
            }
          }
        },
        {
          word: 'arbor', gender: 'F', showDeclension: false, image: require('../assets/tree.png'),
          declension: {
            nominative: {
              singular: 'arbor',
              plural: 'arborēs'
            },
            genitive: {
              singular: 'arboris',
              plural: 'arborum'
            },
            dative: {
              singular: 'arborī',
              plural: 'arboribus'
            },
            accusative: {
              singular: 'arborem',
              plural: 'arborēs'
            },
            ablative: {
              singular: 'arbore',
              plural: 'arboribus'
            }
          }
        },
        {
          word: 'manus', gender: 'F', showDeclension: false, image: require('../assets/hand.png'),
          declension: {
            nominative: {
              singular: 'manus',
              plural: 'manūs'
            },
            genitive: {
              singular: 'manūs',
              plural: 'manuum'
            },
            dative: {
              singular: 'manuī',
              plural: 'manibus'
            },
            accusative: {
              singular: 'manum',
              plural: 'manūs'
            },
            ablative: {
              singular: 'manū',
              plural: 'manibus'
            }
          }
        },
        {
          word: 'glaciēs', gender: 'F', showDeclension: false, image: require('../assets/ice.png'),
          declension: {
            nominative: {
              singular: 'glaciēs',
              plural: 'glaciēs'
            },
            genitive: {
              singular: 'glaciēī',
              plural: 'glaciērum'
            },
            dative: {
              singular: 'glaciēī',
              plural: 'glaciēbus'
            },
            accusative: {
              singular: 'glaciem',
              plural: 'glaciēs'
            },
            ablative: {
              singular: 'glaciē',
              plural: 'glaciēbus'
            }
          }
        },
        {
          word: 'mālum', gender: 'N', showDeclension: false, image: require('../assets/apple.png'),
          declension: {
            nominative: {
              singular: 'mālum',
              plural: 'māla'
            },
            genitive: {
              singular: 'mālī',
              plural: 'mālōrum'
            },
            dative: {
              singular: 'mālō',
              plural: 'mālīs'
            },
            accusative: {
              singular: 'mālum',
              plural: 'māla'
            },
            ablative: {
              singular: 'mālō',
              plural: 'mālīs'
            }
          }
        },
          {
            word: 'liber', gender: 'M', showDeclension: false, image: require('../assets/book.png'),
            declension: {
              nominative: {
                singular: 'liber',
                plural: 'librī'
              },
              genitive: {
                singular: 'librī',
                plural: 'librōrum'
              },
              dative: {
                singular: 'librō',
                plural: 'librīs'
              },
              accusative: {
                singular: 'librum',
                plural: 'librōs'
              },
              ablative: {
                singular: 'librō',
                plural: 'librīs'
              }
            }
          },
            {
              word: 'agricola', gender: 'M', showDeclension: false, image: require('../assets/farmer.png'),
              declension: {
                nominative: {
                  singular: 'agricola',
                  plural: 'agricolae'
                },
                genitive: {
                  singular: 'agricolae',
                  plural: 'agricolārum'
                },
                dative: {
                  singular: 'agricolae',
                  plural: 'agricolīs'
                },
                accusative: {
                  singular: 'agricolam',
                  plural: 'agricolās'
                },
                ablative: {
                  singular: 'agricolā',
                  plural: 'agricolīs'
                }
              }
            },
            {
              word: 'gladius', gender: 'M', showDeclension: false, image: require('../assets/gladius.png'),
              declension: {
                nominative: {
                  singular: 'gladius',
                  plural: 'gladiī'
                },
                genitive: {
                  singular: 'gladiī',
                  plural: 'gladiōrum'
                },
                dative: {
                  singular: 'gladiō',
                  plural: 'gladiīs'
                },
                accusative: {
                  singular: 'gladium',
                  plural: 'gladiōs'
                },
                ablative: {
                  singular: 'gladiō',
                  plural: 'gladiīs'
                }
              }
            },
            {
              word: 'equus', gender: 'M', showDeclension: false, image: require('../assets/horse.png'),
              declension: {
                nominative: {
                  singular: 'equus',
                  plural: 'equī'
                },
                genitive: {
                  singular: 'equī',
                  plural: 'equōrum'
                },
                dative: {
                  singular: 'equō',
                  plural: 'equīs'
                },
                accusative: {
                  singular: 'equum',
                  plural: 'equōs'
                },
                ablative: {
                  singular: 'equō',
                  plural: 'equīs'
                }
              }
            },
            {
              word: 'pecūnia', gender: 'F', showDeclension: false, image: require('../assets/money.png'),
              declension: {
                nominative: {
                  singular: 'pecūnia',
                  plural: 'pecūniae'
                },
                genitive: {
                  singular: 'pecūniae',
                  plural: 'pecūniārum'
                },
                dative: {
                  singular: 'pecūniae',
                  plural: 'pecūniīs'
                },
                accusative: {
                  singular: 'pecūniam',
                  plural: 'pecūniās'
                },
                ablative: {
                  singular: 'pecūniā',
                  plural: 'pecūniīs'
                }
              }
            },
      ]
    }
  },
  
  methods: {
    
  },
  beforeMount() {
    this.nouns = shuffle(this.nouns);
  }
}
</script>

<style>
* {
  font-family: 'American Typewriter', serif;
}

#noun-list {
  list-style-type: none;
  display: flex;
  flex-wrap: wrap;
}

.noun-card {
  border: 1px solid;
  text-align: center;
  min-width: 315px;
  padding: 20px;
  margin: 5px;
  overflow: hidden;
}

.word {
  font-size: 30px;
}

.gender {
  font-style: italic;
  text-transform: lowercase;
  font-size: 28px;
}

.image {
  width: 100px;
  height: 100px;
}

.declension-table {
  margin-top: 10px;
}

.fade-enter-active, .fade-leave-active {
  transition: all 1.5s;
  max-height: 600px;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  max-height: 0px;
  opacity: 0;
}

</style>
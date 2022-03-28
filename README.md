# datamuse_prova
import json,requests
from pprint import pprint

keyword = st.text_input('GIve me a word', 'word')

option = st.selectbox(
     'What do you want to know about this word?',
     ('Words that have similar meaning', 'Words that sound similarly', 'Some synonyms', 'Some antonyms'))
st.write('You selected:', option)
filter = ' '
if option == 'Words that have similar meaning':
  filter = 'ml='
elif option == 'Words that sound similarly':
  filter = 'sl='
elif option == 'Some synonyms':
  filter = 'rel_syn='
elif option == 'Some antonyms':
  filter = 'rel_ant='
else:
  pass

url= 'https://api.datamuse.com/words?' + filter + keyword + '&max=10'
response = requests.get(url)  
dataFromDatamuse = json.loads(response.text) 
st.write(dataFromDatamuse)

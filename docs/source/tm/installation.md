# நிறுவல்

நீங்கள் தொடங்குவதற்கு முன், தகுந்த தொகுப்புகளை நிறுவுவதன் மூலம் உங்கள் சூழலை அமைக்க வேண்டும்.

`huggingface_hub` **Python 3.8+** மின்பொருள்களில் சோதிக்கப்பட்டுள்ளது.

### பிப் மூலம் நிறுவு

**pip மூலம் நிறுவல்**

`huggingface_hub`-ஐ ஒரு [மெய்நிகர் சூழலில்](https://docs.python.org/3/library/venv.html) (virtual environment) நிறுவுவது மிகவும் பரிந்துரைக்கப்படுகிறது. நீங்கள் பைதான்  மெய்நிகர் சூழல்களைக் குறித்து அறியாதவராக இருந்தால், இந்த [வழிகாட்டலைப்](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/)பார்க்கவும். ஒரு மெய்நிகர் சூழல் பல்வேறு திட்டங்களை எளிதில் நிர்வகிக்கவும், சார்புகளுக்கிடையிலான (dependencies) இணக்கமின்மை பிரச்சனைகளைத் தவிர்க்கவும் உதவுகிறது.

முதலில், உங்கள் திட்ட அடைவரிசையில் (project directory) ஒரு மெய்நிகர் சூழலை உருவாக்கத் தொடங்குங்கள்:

```bash
python -m venv .env
```
மெய்நிகர் சூழலை செயல்படுத்தவும். Linux மற்றும் macOS-இல்:


```bash
source .env/bin/activate
```

விண்டோஸ்-இல் மெய்நிகர் சூழலை செயல்படுத்த:

```bash
.env/Scripts/activate
```

இப்போது நீங்கள் `huggingface_hub`-ஐ [PyPi பதிவகத்திலிருந்து](https://pypi.org/project/huggingface-hub/) நிறுவ தயாராக இருக்கிறீர்கள்.

```bash
pip install --upgrade huggingface_hub
```

முடித்த பிறகு, [நிறுவல் சரியாக வேலை](#check-installation) செய்கிறதா என்பதைச் சோதிக்கவும்.

### விருப்பத் தேவைப்படும் சார்புகளை நிறுவல்**

`huggingface_hub`-இன் சில சார்புகள் விருப்பமானவை, ஏனெனில் அவை `huggingface_hub`-இன் அடிப்படை அம்சங்களை இயக்க தேவையில்லை. எனினும், விருப்பச் சார்புகள் நிறுவப்படாதால், `huggingface_hub`-இன் சில அம்சங்கள் கிடைக்காது.

நீங்கள் விருப்பத் தேவைப்படும் சார்புகளை `pip` மூலம் நிறுவலாம்:

```bash
# டென்சர்‌ஃபிளோவுக்கான குறிப்பிட்ட அம்சங்களுக்கு சார்ந்த பொறுப்பு நிறுவவும்
# /!\ எச்சரிக்கை: இது `pip install tensorflow` க்கு சமமாகக் கருதப்படாது
pip install 'huggingface_hub[tensorflow]'

# டார்ச்-குறிப்பிட்ட மற்றும் CLI-குறிப்பிட்ட அம்சங்களுக்கு தேவையான பொறுப்புகளை நிறுவவும்.
pip install 'huggingface_hub[cli,torch]'
```
`huggingface_hub`-இல் உள்ள விருப்பத் தேவைப்படும் சார்புகளின் பட்டியல்:

- `cli`: `huggingface_hub`-க்கு மிகவும் வசதியான CLI இடைமுகத்தை வழங்குகிறது.
- `fastai`, `torch`, `tensorflow`: வடிவமைப்பு குறிப்பிட்ட அம்சங்களை இயக்க தேவையான சார்புகள்.
- `dev`: நூலகத்திற்கு பங்களிக்க தேவையான சார்புகள். இதில் சோதனை (சோதனைகளை இயக்க), வகை சோதனை (வகை சரிபார்ப்பு ஐ இயக்க) மற்றும் தரம் (லிண்டர்கள் ஐ இயக்க) உள்ளன.

### மூலத்திலிருந்து நிறுவல்

சில சமயம், `huggingface_hub`-ஐ நேரடியாக மூலத்திலிருந்து நிறுவுவது சுவாரஸ்யமாக இருக்கலாம். இது, சமீபத்திய நிலையான பதிப்பு பதிலாக, புதியதாக இருக்கும் `முக்கிய` பதிப்பைப் பயன்படுத்த அனுமதிக்கிறது. `முக்கிய` பதிப்பு, சமீபத்திய முன்னேற்றங்களுடன் புதுப்பிக்க உதவுகிறது, உதாரணமாக, சமீபத்திய அதிகாரப்பூர்வ வெளியீட்டுக்குப் பிறகு பிழை சரிசெய்யப்பட்டிருந்தாலும் புதிய வெளியீடு வந்ததாக இல்லை.

எனினும், இதன் பொருள் `முக்கிய` பதிப்பு எப்போதும் நிலையாக இருக்காது. `முக்கிய` பதிப்பை செயல்படுமாறு வைத்திருக்க நாங்கள் முயற்சிக்கிறோம், மேலும் பெரும்பாலான சிக்கல்களை சில மணி நேரங்கள் அல்லது ஒரு நாளுக்குள் தீர்க்கவேண்டியவை. நீங்கள் ஒரு பிரச்சினையை எதிர்கொண்டால், அதைக் கூட்டுங்கள், அதைக் கூட விரைவில் சரிசெய்ய நாங்கள் முயற்சிக்கிறோம்!


```bash
pip install git+https://github.com/huggingface/huggingface_hub
```

மூலத்திலிருந்து நிறுவும் போது, நீங்கள் குறிப்பிட்ட கிளையை (branch) குறிப்படலாம். இது, இன்னும் இணைக்கப்படாத புதிய அம்சம் அல்லது புதிய பிழை சரிசெய்வுகளை சோதிக்க விரும்பும்போது பயனுள்ளதாக இருக்கும்:


```bash
pip install git+https://github.com/huggingface/huggingface_hub@my-feature-branch
```
முடித்த பிறகு, [நிறுவல் சரியாக வேலை செய்கிறதா]((#check-installation)) என்பதைச் சோதிக்கவும்.

### திருத்தக்கூடிய நிறுவல்

மூலத்திலிருந்து நிறுவுதல் [எடிடேபிள் இன்ஸ்டால்](https://pip.pypa.io/en/stable/topics/local-project-installs/#editable-installs) அமைப்பதற்கு அனுமதிக்கிறது. இது, `huggingface_hub`-க்கு பங்களிக்க திட்டமிட்டு, கோடில் மாற்றங்களை சோதிக்க விரும்பும் போது மேலும் முற்றிலும் மேம்பட்ட நிறுவல் ஆகும். உங்கள் இயந்திரத்தில் `huggingface_hub`-இன் ஒரு உள்ளூர் நகலை கிளோன் செய்ய வேண்டும்.

```bash
# முதலில், கிடுகிடுக்கும் தொகுப்பை உள்ளூர் முறையில் கிளோன் செய்யவும்.
git clone https://github.com/huggingface/huggingface_hub.git

# அதன் பிறகு, -e கொள்கையைப் பயன்படுத்தி நிறுவவும்.
cd huggingface_hub
pip install -e .
```

இந்த கட்டளைகள், நீங்கள் தரவுகளை கிளோன் செய்த அடைவை மற்றும் உங்கள் பைதான் நூலகப் பாதைகளை இணைக்கும். பைதான், தற்போது சாதாரண நூலகப் பாதைகளுக்கு கூட, நீங்கள் கிளோன் செய்த அடைவைப் பார்வையிடும். 

உதாரணமாக, உங்கள் பைதான் தொகுப்புகள் பொதுவாக `./.venv/lib/python3.11/site-packages/` இல் நிறுவப்பட்டிருந்தால், பைதான்n நீங்கள் கிளோன் செய்த `./huggingface_hub/` அடைவையும் தேடுவதாக இருக்கும்.

## கொண்டா மூலம் நிறுவல்

**நீங்கள் அதனுடன் மேலும் பரிச்சயமாக இருந்தால்**, `huggingface_hub`-ஐ [conda-forge சேனல்](https://anaconda.org/conda-forge/huggingface_hub) பயன்படுத்தி நிறுவலாம்:

```bash
conda install -c conda-forge huggingface_hub
```

முடித்த பிறகு, [நிறுவல் சரியாக வேலை செய்கிறதா என்பதைச் சோதிக்கவும்](#check-installation).

## நிறுவலைச் சோதிக்கவும்

நிறுவலுக்குப் பிறகு, `huggingface_hub` சரியாக வேலை செய்கிறதா என்பதைக் கீழ்காணும் கட்டளையை இயக்கி சோதிக்கவும்:

```bash
python -c "from huggingface_hub import model_info; print(model_info('gpt2'))"
```

இந்த கட்டளை, Hub-இல் உள்ள [gpt2](https://huggingface.co/gpt2) மாடலுக்கான தகவல்களை பெறும். வெளியீடு கீழ்காணும் மாதிரியாக இருக்க வேண்டும்:


```text
Model Name: gpt2
Tags: ['pytorch', 'tf', 'jax', 'tflite', 'rust', 'safetensors', 'gpt2', 'text-generation', 'en', 'doi:10.57967/hf/0039', 'transformers', 'exbert', 'license:mit', 'has_space']
Task: text-generation
```

## Windows மரபுகள்

எந்த இடத்திலும் சிறந்த ML-ஐ பொதுமக்களுக்கு வழங்கும் எங்கள் இலக்குடன், `huggingface_hub`-ஐ ஒரு குறைவில்லாத தளத்துடன் உருவாக்கினோம் மற்றும் குறிப்பாக Unix அடிப்படையிலான மற்றும் Windows அமைப்புகளில் சரியாக செயல்படவும். ஆனால், Windows-இல் இயங்கும் போது `huggingface_hub`-க்கு சில வரையறைகள் உள்ளன. இங்கே தெரிந்த சிக்கல்களின் முழு பட்டியல் உள்ளது. உங்கள் சந்தர்ப்பத்தில் ஆவணமிடாத சிக்கல் கண்டுபிடித்தால், [Github-ல் ஒரு பிரச்சனை திறக்க](https://github.com/huggingface/huggingface_hub/issues/new/choose) எங்களுக்கு தெரிவிக்கவும்.

- `huggingface_hub`-இன் காசே  அமைப்பு, Hub-இல் இருந்து பதிவிறக்கம் செய்யப்பட்ட கோப்புகளைச் சரியாக காசே செய்ய சிம்லிங்குகளை  நம்புகிறது. Windows-இல், சிம்லிங்குகளை இயக்குவதற்கு நீங்கள் டெவலப்பர் முறை  அல்லது உங்கள் ஸ்கிரிப்டைப் ஆட்மின்  ஆக இயக்க வேண்டும். சிம்லிங்குகள் இயக்கப்படாவிட்டால், காசே அமைப்பு இன்னும் வேலை செய்யும் ஆனால் சரியாக செயல்படாது. மேலும் விவரங்களுக்கு [காசே வரையறைகள்](./guides/manage-cache#limitations) பகுதியைப் படிக்கவும்.
- Hub-இல் கோப்பு பாதைகள் சிறப்பு எழுத்துக்கள் கொண்டதாக இருக்கலாம் (எ.கா. `"path/to?/my/file"`). Windows, [சிறப்பு எழுத்துக்கள்](https://learn.microsoft.com/en-us/windows/win32/intl/character-sets-used-in-file-names) மீது அதிக கட்டுப்பாடுகளை கொண்டுள்ளது, இது Windows-இல் அந்த கோப்புகளை பதிவிறக்கம் செய்ய முடியாததாக உருவாக்குகிறது. இது நிச்சயமாக ஒரு புலவியல் சந்தர்ப்பமாக இருக்க வேண்டும். இது தவறு என்று நீங்கள் நினைத்தால், அதற்கான தீர்வைத் தேட எங்களை அணுகவும்.

## அடுத்த கட்டங்கள்

`huggingface_hub` உங்கள் இயந்திரத்தில் முறையாக நிறுவப்பட்ட பிறகு, [சூழல் மாறிலிகளை](package_reference/environment_variables) கட்டமைக்க அல்லது [எங்கள் வழிகாட்டிகளில்](guides/overview) ஒன்றைப் பார்வையிட தேவையெனில், தொடங்குங்கள்.
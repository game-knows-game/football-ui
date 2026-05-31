# Football Predictor UI

A web-based frontend for the **Data-Driven Football Forecasting** neural network predictor.

## Setup

1. **Install dependencies** (use the same Python environment as `football-predictor`):

```bash
pip install flask flask-cors
```

> The other dependencies (torch, pandas, numpy, scikit-learn) should already be installed from the `football-predictor` project.

2. **Ensure the backend is trained** — you need the artifacts:
   - `../football-predictor/artifacts/model_best.pt`
   - `../football-predictor/artifacts/scalers.pkl`
   - `../football-predictor/data/epl/*.csv`

3. **Run the server**:

```bash
python server.py
```

4. **Open** [http://localhost:5000](http://localhost:5000) in your browser.

## Features

- **Team Autocomplete** — search and select teams from the dataset
- **Date Picker** — choose a match date for temporal context
- **Outcome Probabilities** — animated bars showing H/D/A probabilities
- **Predicted Score** — rounded goals plus raw xG values
- **Match Statistics** — shots, corners, fouls, cards, HT goals
- **Recent Form** — last 5 matches for each team before the selected date

## Architecture

```
football-ui/
├── server.py                # Flask API (wraps nn_football.predict)
├── requirements.txt
├── README.md
└── static/
    ├── index.html           # Single-page frontend
    ├── style.css            # Dark theme stylesheet
    └── app.js               # Client-side logic
```

The Flask server imports `nn_football` directly from the sibling `football-predictor` directory, so no duplication of the model code is needed.

```
from flask import Flask, jsonify, request
import random
from datetime import datetime, timedelta
import time

app = Flask(__name__)

sample_data1 = {
    "name": ["Alice", "Bob", "Charlie", "David", "Eve"],
    "age": [25, 30, 35, 40, 45],
    "city": ["New York", "Los Angeles", "Chicago", "Houston", "Phoenix"]
}

sample_data2 = {
    "name": ["Frank", "Grace", "Heidi", "Ivan", "Judy"],
    "age": [28, 33, 38, 43, 48],
    "city": ["Miami", "Dallas", "Seattle", "Denver", "Boston"]
}

sample_data3 = {
    "name": ["Kate", "Leo", "Mia", "Nina", "Oscar"],
    "age": [22, 27, 32, 37, 42],
    "city": ["San Francisco", "San Diego", "Las Vegas", "Orlando", "Atlanta"]
}

@app.route('/random_json', methods=['GET'])
def random_json():
    dataset_key = request.args.get('key')
    from_time = request.args.get('from')
    to_time = request.args.get('to')

    if from_time is None or to_time is None:
        return jsonify({"error": "from and to parameters are required"}), 400

    try:
        from_timestamp = int(from_time) / 1000
        to_timestamp = int(to_time) / 1000
    except ValueError:
        return jsonify({"error": "from and to parameters must be valid epoch milliseconds"}), 400

    if dataset_key == 'aaa':
        sample_data = sample_data1
    elif dataset_key == 'bbb':
        sample_data = sample_data2
    else:
        sample_data = sample_data3

    current_time = from_timestamp
    data_points = []

    while current_time <= to_timestamp:
        data_points.append({
            "name": random.choice(sample_data["name"]),
            "age": random.choice(sample_data["age"]),
            "city": random.choice(sample_data["city"]),
            "timestamp": datetime.fromtimestamp(current_time).isoformat()
        })
        current_time += 5  # 5秒間隔

    return jsonify(data_points)

if __name__ == '__main__':
    app.run(debug=True)
```

from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/")
def home():
    return jsonify({"message": "AI Virtual Try-On API is Running!"})

@app.route("/try-on", methods=["POST"])
def try_on():
    if "user_image" not in request.files:
        return jsonify({"error": "No file uploaded"}), 400

    file = request.files["user_image"]
    return jsonify({"message": "Try-On Successful (Placeholder)", "filename": file.filename})

if __name__ == "__main__":
    app.run(debug=True, host="0.0.0.0", port=8000)

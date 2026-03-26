# ProyectoIHC
Proyecto de interfaz que emplea IHC para la materia de Interacción Humano - Computadora

from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/accion", methods=["POST"])
def accion():
    data = request.get_json()
    comando = data.get("comando", "").lower()

    if comando == "iniciar":
        respuesta = "Proceso iniciado"
    elif comando == "detener":
        respuesta = "Proceso detenido"
    elif comando == "reiniciar":
        respuesta = "Proceso reiniciado"
    else:
        respuesta = "Comando no reconocido"

    return jsonify({"respuesta": respuesta})

if __name__ == "__main__":
    app.run(debug=True)

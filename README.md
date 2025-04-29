from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

# Aquí guardamos los usuarios en una lista
usuarios = []

class Usuario(BaseModel):
    nombre: str
    email: str

# POST para crear un usuario
@app.post("/usuario")
def crear_usuario(usuario: Usuario):
    usuarios.append(usuario)
    return {"mensaje": "Usuario creado exitosamente"}

# GET para obtener usuarios
@app.get("/usuarios")
def obtener_usuarios():
    return usuarios

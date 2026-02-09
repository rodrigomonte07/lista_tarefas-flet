import flet as ft

lista_de_tarefas = []

def main(pagina:ft.Page):
    pagina.title = "LISTA DE TAREFAS"

    def adicionar_tarefa(e):
        nova_tarefa = entrada_nome_tarefa.value.strip()
        if nova_tarefa:
            lista_de_tarefas.append(nova_tarefa)
            entrada_nome_tarefa.value = ""
            atualizar_lista()
            pagina.update()

    def atualizar_lista():
        container_lista.controls.clear()
        for tarefa in lista_de_tarefas:
            container_lista.controls.append(ft.Text(f"-{tarefa}"))

    mensagem = ft.Text(value="TAREFAS", color="#1E5E09")
    entrada_nome_tarefa = ft.TextField(label="Nome da tarefa")
    botao = ft.ElevatedButton(text="Adicionar tarefa", on_click=adicionar_tarefa)
    container_lista = ft.Column(spacing=5)
    
    pagina.add(mensagem, entrada_nome_tarefa, botao, container_lista)


ft.app(target=main)

package main

import (
        "fmt"
        //"os"
        "os/exec"
        "github.com/rivo/tview"
)

func makeDir(dir string, user string) {
        out, err := exec.Command("mkdir", dir).Output()

        if err != nil {
                fmt.Printf("%s", err)
        }

        fmt.Println("Foi.")
        output := string(out[:])
        fmt.Println(output)

        out, err = exec.Command("chown", "-R", user, dir+"/").Output()

        if err != nil {
                fmt.Printf("%s", err)
        }

        fmt.Println("Foi.")
        output = string(out[:])
        fmt.Println(output)
}


func main() {
        app := tview.NewApplication()

        form := tview.NewForm()
        list := tview.NewList()

        form.AddInputField("Usuário" , "Test", 20, tview.InputFieldMaxLength(20), func(txt string){} )
        form.AddButton("Cadastrar", func() {
                app.SetFocus(list)
        })
        form.SetTitle("Cadastrar")
        form.SetBorder(true)

        list.AddItem("Acari","/storages/acari",'a', nil)
        list.AddItem("Caico","/storages/caico",'b', func() { app.SetFocus(form) } )
        list.AddItem("Sair","Fechar aplicação",'q', func() { app.Stop() })

        list.SetTitle("Storages")
        list.SetBorder(true)

        flex := tview.NewFlex()
        flex.AddItem(list, 0, 1, true)
        flex.AddItem(form, 0, 1, false)

        if err := app.SetRoot(flex, true).SetFocus(flex).Run(); err != nil {
                panic(err)
        }

        //makeDir(os.Args[1], os.Args[2])
}

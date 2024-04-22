## Include VerificacaoPlataforma SA:MP

Este � um include que tem a fun��o de verificar se o jogador est� usando um `mobile` ou um `computador`. Leia as categorias abaixo para se manter informado.

English > [README](https://github.com/ocalasans/Verificacao-Plataforma/blob/main/README.eng.md).

-----------------------

### Como instalar?

Voc� deve fazer o download do include. Depois de t�-lo feito, voc� dever� colocar o include na pasta (pawno > include). Ap�s ter feito isso, abra o arquivo pwn do seu Gamemode e coloque o seguinte c�digo abaixo dos seus outros includes:
```pawn
#include <VerificacaoPlataforma>
```

-----------------------

### Include necess�ria

* [Pawn.RakNet](https://github.com/katursis/Pawn.RakNet).

> [!WARNING]
> Se o usu�rio n�o tiver ativado a biblioteca [Pawn.RakNet](https://github.com/katursis/Pawn.RakNet), receber� um erro de n�mero `111`.

-----------------------

### Como funciona?

Assim que o jogador se conecta ao servidor, o include automaticamente verifica em qual plataforma ele est�, seja `mobile` ou `computador`, com a assist�ncia do [Pawn.RakNet](https://github.com/katursis/Pawn.RakNet). Para conferir a plataforma do jogador, basta utilizar a fun��o booleana `IsPlayerAndroid`. Abaixo, est�o alguns exemplos:

Com o `if`
```pawn
CMD:plataforma(playerid)
{
    new bool:isAndroid, bool:haveAutoaim;
    GetPlayerPlataformInfo(playerid, isAndroid, haveAutoaim);
    //
    if(isAndroid)
        SendClientMessage(playerid, 0xFFFFFFFF, "Voce esta conectado pela plataforma Mobile.");
    //
    else if(!isAndroid) // Pode ser somente else.
        SendClientMessage(playerid, 0xFFFFFFFF, "Voce esta conectado pela plataforma Computador.");
    //
    return true;
}
```

Sem o `if`
```pawn
CMD:plataforma(playerid)
{
    new string[128], bool:isAndroid, bool:haveAutoaim;
    GetPlayerPlataformInfo(playerid, isAndroid, haveAutoaim);
    //
    format(string, sizeof(string), "Voce esta conectado pela plataforma %s.", isAndroid ? ("Mobile") : ("Computador"));
    SendClientMessage(playerid, 0xFFFFFFFF, string);
    //
    return true;
}
```

-----------------------

Este include tamb�m possui uma fun��o chamada `PlayerHasAutoAim`. Essa fun��o consiste em verificar se o jogador est� com mira autom�tica ou se est� sem a mira autom�tica, conhecida como `LockOn`. Abaixo, est�o alguns exemplos:

Com o `if`
```pawn
CMD:mira(playerid)
{
    new bool:isAndroid, bool:haveAutoaim;
    GetPlayerPlataformInfo(playerid, isAndroid, haveAutoaim);
    //
    if(haveAutoaim)
        SendClientMessage(playerid, 0xFFFFFFFF, "Sua mira automatica esta Ativada.");
    //
    else if(!haveAutoaim) // Pode ser somente else.
        SendClientMessage(playerid, 0xFFFFFFFF, "Sua mira automatica esta Desativada.");
    //
    return true;
}
```

Sem o `if`
```pawn
CMD:mira(playerid)
{
    new string[128], bool:isAndroid, bool:haveAutoaim;
    //
    format(string, sizeof(string), "Sua mira automatica esta %s.", haveAutoaim(playerid) ? ("Ativada") : ("Desativada"));
    SendClientMessage(playerid, 0xFFFFFFFF, string);
    //
    return true;
}
```

-----------------------

### Informa��es de contato

Instagram: [ocalasans](https://instagram.com/ocalasans)   
YouTube: [Calasans](https://www.youtube.com/@ocalasans)   
Discord: ocalasans   
Comunidade: [SA:MP Programming Community�](https://abre.ai/samp-spc)
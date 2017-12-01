---
title: "方法: どの .NET Framework のセキュリティ更新プログラムと修正プログラムがインストールされている確認"
description: "どの .NET Framework のセキュリティ更新プログラムと修正プログラムがコンピューターにインストールされているを確認する方法を説明します。"
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c35705470a8e1b553eca2ca0c68d3b8b9b3f6fa6
ms.sourcegitcommit: a3ba258f7a8cab5c6d19a3743dd95e904ecebc44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>方法: どの .NET Framework のセキュリティ更新プログラムと修正プログラムがインストールされている確認

ここで説明する .NET Framework のセキュリティ更新プログラムを確認する方法と修正プログラムがコンピューターにインストールされています。

> [!NOTE]
> この記事で示したすべての手法では、管理者特権を持つアカウントが必要です。

## <a name="to-find-installed-updates-using-the-registry"></a>インストールされたレジストリを使用して更新プログラムを検索するには

インストールされているセキュリティ更新プログラムと修正プログラムをコンピューターにインストールされている .NET Framework のバージョンごとには、Windows レジストリに一覧表示されます。 レジストリ エディターを使用することができます (*regedit.exe*) プログラムをこの情報を表示します。

1. プログラム **regedit.exe** を開きます。 Windows 8 およびそれ以降のバージョンを右クリックして**開始** ![Windows ロゴ](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")選択してから、**実行**です。 **開く**ボックスに、入力**regedit**選択**[ok]**です。

2. レジストリ エディターで、次のサブキーを開きます。

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     インストールされている更新プログラムは、適用された .NET Framework バージョンを識別するサブキーの下に一覧表示されています。 各更新プログラムは、サポート技術情報の (KB) 番号で識別されます。

レジストリ エディターでは、各バージョンの .NET Framework バージョンとインストールされている更新プログラムが別々のサブキーに格納されます。 インストールされているバージョン番号を検出する方法については、次を参照してください。[する方法: .NET Framework バージョンがインストールされている確認](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)です。

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>コードでレジストリを照会することによってインストールされた更新プログラムを検索するには

次の例は、プログラムによって、.NET Framework のセキュリティ更新プログラムと、コンピューターにインストールされている修正プログラムを決定します。

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

この例には、次のいずれかのような出力が生成されます。

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>PowerShell でレジストリを照会してインストールされた更新プログラムを検索するには

次の例では、.NET Framework のセキュリティ更新プログラムと PowerShell を使用してコンピューターにインストールされている修正プログラムを確認する方法を示します。

```powershell
 Get-ChildItem "HKLM:SOFTWARE\Wow6432Node\Microsoft\Updates\*" -Recurse | Where-Object {$_.name -like
 "*.NET Framework*"}
```

この例には、次のいずれかのような出力が生成されます。

```console
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Client Profile


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y


    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Extended


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y
```

## <a name="see-also"></a>関連項目

[方法: .NET Framework バージョンがインストールされている確認](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[開発者にとっての .NET Framework をインストールします。](../../../docs/framework/install/guide-for-developers.md)  
[バージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)

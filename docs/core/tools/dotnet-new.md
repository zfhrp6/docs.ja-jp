---
title: "dotnet-new コマンド | Microsoft Docs"
description: "dotnet-new コマンドは、現在のディレクトリに新しい .NET Core プロジェクトを作成します。"
keywords: "dotnet-new, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 263c3d05-3a47-46a6-8023-3ca16b488410
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: a49fe94ca8f678c614fb7f58767693c73e34c737

---

#<a name="dotnet-new"></a>dotnet-new

> [!WARNING]
> このトピックは .NET Core Tools Preview 2 を対象としています。 .NET Core Tools RC4 バージョンについては、「[dotnet-new (.NET Core Tools RC4)](../preview3/tools/dotnet-new.md)」トピックを参照してください。

## <a name="name"></a>名前
`dotnet-new` -- 現在のディレクトリに新しい .NET Core プロジェクトを作成します。

## <a name="synopsis"></a>構文
`dotnet new [--help] [--type] [--lang]`

## <a name="description"></a>説明
`dotnet new` コマンドは、コマンド ライン インターフェイス (CLI) ツールセットを試すために有効な .NET Core プロジェクトとサンプル ソース コードを初期化するのに便利です。 

このコマンドは、ディレクトリのコンテキストで呼び出されます。 このコマンドが呼び出されると、以下の&2; つの主な成果物が現在のディレクトリにドロップされます。 

1. サンプルの "Hello World" プログラムを含む `Program.cs` (または `Program.fs`) ファイル。
2. 有効な `project.json` ファイル。

その後、プロジェクトをコンパイルし、さらに編集することができます。 

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-l|--lang <C#|F#>`

プロジェクトの言語です。 既定値は `C#` です。 他の有効値は `csharp`、`fsharp`、`cs`、`fs` です。

`-t|--type`

プロジェクトの種類です。 C# の場合の有効値は `console`、`web`、`lib`、`xunittest` で、F# の場合は `console` のみが有効です。 

## <a name="examples"></a>例

現在のディレクトリに、C# コンソール アプリケーション プロジェクトを作成します。

`dotnet new` または `dotnet new --lang c#` 
   
現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。

`dotnet new --lang f#`
  
現在のディレクトリに、新しい ASP.NET Core C# アプリケーション プロジェクトを作成します。

`dotnet new -t web`


<!--HONumber=Feb17_HO2-->



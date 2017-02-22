---
title: "dotnet-new コマンド | Microsoft Docs"
description: "dotnet-new コマンドは、現在のディレクトリに新しい .NET Core プロジェクトを作成します。"
keywords: "dotnet-new, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 02/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
translationtype: Human Translation
ms.sourcegitcommit: 96fd8ea3e55ea33e0bdd0bf3c50a10d0de6db1a1
ms.openlocfilehash: f0c62647c5817db2057c60a7a95a62f08f7889a5

---
#<a name="dotnet-new-net-core-tools-rc4"></a>dotnet-new (.NET Core Tools RC4)

> [!WARNING]
> このトピックは .NET Core Tools RC4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[dotnet-new](../../tools/dotnet-new.md)」トピックを参照してください。

## <a name="name"></a>名前
dotnet-new - 現在のディレクトリに新しい .NET Core プロジェクトを作成します。

## <a name="synopsis"></a>構文
```
dotnet new [template] [-lang|--language] [-n|--name] [-o|--output] [-h|--help]
dotnet new [template] [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>説明
`dotnet new` コマンドは、コマンドライン インターフェイス (CLI) ツールセットを試すために有効な .NET Core プロジェクトとサンプル ソース コードを初期化するのに便利です。 

このコマンドは、ディレクトリのコンテキストで呼び出されます。 呼び出されると、コマンドに渡されたテンプレートとオプションに基づき、リソースとファイルが用意されます。 

その後、プロジェクトをコンパイルし、さらに編集することができます。 

## <a name="arguments"></a>引数
template - コマンドが呼び出されたときにインスタンス化するテンプレート。

このコマンドには、テンプレートの規定の一覧が含まれます。`dotnet new --help` を使用してください。 

## <a name="options"></a>オプション

`-l|--list`         

指定した名前を含むテンプレートを一覧表示します。

`-lang|--language`  

作成するテンプレートの言語を指定します。

`-n|--name`         

作成される出力の名前。 名前が指定されていない場合、現在のディレクトリの名前が使用されます。

`-o|--output`       

生成された出力を配置する場所。

`-all|--show-all`   

特定の種類のプロジェクトのテンプレートをすべて表示します。

`-h|--help`

コマンドのヘルプを印刷します。

## <a name="template-options"></a>テンプレート オプション
プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。 たとえば、コア テンプレートの場合、次のオプションが与えられています。

**console、xunit、mstest**

`-f|--framework` - ターゲットにするフレームワークを指定します。 値: netcoreapp1.0 または netcoreapp1.1 (既定: netcoreapp1.0)

**web、webapi**

`-f|--framework` - ターゲットにするフレームワークを指定します。 値: netcoreapp1.0 または netcoreapp1.1 (既定: netcoreapp1.0)
 
**mvc**

`-f|--framework` - ターゲットにするフレームワークを指定します。 値: netcoreapp1.0 または netcoreapp1.1 (既定: netcoreapp1.0)

`-au|--authentication` -  使用する認証の種類。 値: なしまたは個別 (既定: なし)

`-uld|--use-local-db` - SQLite の代わりに LocalDB を使用するかどうか。 値: true または false (既定: false)

**classlib**

`-f|--framework` - ターゲットにするフレームワークを指定します。 値: netcoreapp1.0、netcoreapp1.1、netstandard1.0 - 1.6 (既定: netstandard1.4)。

## <a name="examples"></a>例

現在のディレクトリに F# コンソール アプリケーション プロジェクトを作成します。

`dotnet new console -lang f#` 
   
現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。.NET Core 1.0 を対象にする認証はありません。  

`dotnet new mvc -au None -f netcoreapp1.0`
 
.NET Core 1.1 を対象にする新しい XUnit アプリケーションを作成します。

`dotnet new xunit --Framework netcoreapp1.1`

MVC に利用できるすべてのテンプレートを一覧表示します。

`dotnet new mvc -l`


<!--HONumber=Feb17_HO3-->



---
title: "dotnet-msbuild コマンド | .NET Core SDK"
description: "dotnet-msmsbuild コマンドは、MSmsbuild コマンドラインへのアクセスを提供します"
keywords: "dotnet-msmsbuild, CLI, CLI コマンド, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: cde9d9577246a9025d646ce2a6d574a18512146e
ms.openlocfilehash: 51a3afdcf591b8147790d78471c6fee63ceb7f2d

---

#<a name="dotnet-msbuild"></a>dotnet-msbuild

## <a name="name"></a>名前 
dotnet-msbuild -- プロジェクトとそのすべての依存関係をビルドします。 

## <a name="synopsis"></a>構文

`dotnet msbuild <msbuild_arguments>`

## <a name="description"></a>説明
`dotnet msbuild` コマンドでは、完全に機能する MSBuild へのアクセスを許可します。 

このコマンドには、既存の MSBuild コマンド ライン クライアントとまったく同じ機能があります。 オプションはすべて同じです。 [既存のドキュメント](https://msdn.microsoft.com/en-us/library/ms164311.aspx) を使用して、コマンド リファレンスに慣れることができます。 

## <a name="examples"></a>例

プロジェクトとその依存関係をビルドします。

`dotnet msbuild`

リリース構成を使用して、プロジェクトとその依存関係をビルドします。

`dotnet msbuild /p:Configuration=Release`

発行先を実行して、RID `osx.10.11-x64` に発行します。

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`



<!--HONumber=Nov16_HO3-->



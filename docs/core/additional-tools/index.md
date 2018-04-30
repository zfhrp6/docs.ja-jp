---
title: .NET Core の追加ツール
description: .NET Core 機能を支援し、拡張する追加ツールの概要。
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.custom: mvc
ms.workload:
- dotnetcore
ms.openlocfilehash: 2e33cdbcbe9c81e6c3af84f8f2795ee3dc6e28ae
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-additional-tools"></a>.NET Core の追加ツール

このセクションでは、[.NET Core コマンドライン インターフェイス (CLI)](..\tools\index.md) ツールに加え、.NET Core 機能を支援し、拡張するツールを一覧で紹介します。

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web サービス リファレンス](wcf-web-service-reference-guide.md)

WCF Web サービス リファレンスは Visual Studio に接続されているサービス プロバイダーです。[Visual Studio 2017 バージョン 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools) から導入されました。 このツールは現在のソリューションの Web サービスから、ネットワーク上の場所で、あるいは WSDL ファイルからメタデータを取得し、Web サービスのアクセスに使用できる Windows Communication Foundation (WCF) クライアント プロキシ コードを含む、.NET Core 互換ソース ファイルを生成します。

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML シリアライザー ジェネレーター](xml-serializer-generator.md)

.NET Framework の [Xml シリアライザー ジェネレーター (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) と同様に、[Microsoft.XmlSerializer.Generator NuGet パッケージ](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)は .NET Core および .NET Standard ライブラリのソリューションです。 アセンブリに含まれる型の XML シリアル化アセンブリを作成することで、<xref:System.Xml.Serialization.XmlSerializer> を使用してその型のオブジェクトをシリアル化または逆シリアル化するときの XML シリアル化の起動パフォーマンスを改善します。
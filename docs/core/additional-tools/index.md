---
title: .NET Core の追加ツール
description: .NET Core 機能を支援し、拡張する追加ツールの概要。
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: 5f744fd63116ac453a2a7db8eb94f12738c95f21
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315200"
---
# <a name="net-core-additional-tools"></a>.NET Core の追加ツール

このセクションでは、[.NET Core コマンドライン インターフェイス (CLI)](..\tools\index.md) ツールに加え、.NET Core 機能を支援し、拡張するツールを一覧で紹介します。

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web Service Reference ツール](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web Service Reference は、Visual Studio に接続されているサービス プロバイダーです。[Visual Studio 2017 バージョン 15.5](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools) から導入されました。 このツールは現在のソリューションの Web サービスから、ネットワーク上の場所で、あるいは WSDL ファイルからメタデータを取得し、.NET Core と互換性のあるソース ファイルを生成し、Web サービス操作のアクセスに使用できるメソッドで WCF プロキシ クラスを定義します。

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet-svcutil ツール](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) dotnet-svcutil ツールは、ネットワーク上の場所で Web サービスから、あるいは WSDL ファイルからメタデータを取得し、.NET Core と互換性があるソース ファイルを生成して、Web サービス操作のアクセスに使用できるメソッドで WCF プロキシ クラスを定義する .NET Core CLI ツールです。 **dotnet-svcutil** ツールは、Visual Studio 2017 v15.5 で最初に用意された Visual Studio 接続済みサービス プロバイダーである、[**WCF Web Service Reference**](/dotnet/core/additional-tools/wcf-web-service-reference-guide) に対する代わりのオプションです。 .NET Core CLI ツールとしての **dotnet-svcutil** ツールは、Linux、macOS、および Windows 上で利用可能なクロスプラットフォームです。

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML シリアライザー ジェネレーター](xml-serializer-generator.md)

.NET Framework の [Xml シリアライザー ジェネレーター (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) と同様に、[Microsoft.XmlSerializer.Generator NuGet パッケージ](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)は .NET Core および .NET Standard ライブラリのソリューションです。 アセンブリに含まれる型の XML シリアル化アセンブリを作成することで、<xref:System.Xml.Serialization.XmlSerializer> を使用してその型のオブジェクトをシリアル化または逆シリアル化するときの XML シリアル化の起動パフォーマンスを改善します。
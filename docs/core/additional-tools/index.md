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
# <a name="net-core-additional-tools"></a><span data-ttu-id="c1446-103">.NET Core の追加ツール</span><span class="sxs-lookup"><span data-stu-id="c1446-103">.NET Core additional tools</span></span>

<span data-ttu-id="c1446-104">このセクションでは、[.NET Core コマンドライン インターフェイス (CLI)](..\tools\index.md) ツールに加え、.NET Core 機能を支援し、拡張するツールを一覧で紹介します。</span><span class="sxs-lookup"><span data-stu-id="c1446-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the [.NET Core command-line interface (CLI)](..\tools\index.md) tools.</span></span>

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[<span data-ttu-id="c1446-105">WCF Web Service Reference ツール</span><span class="sxs-lookup"><span data-stu-id="c1446-105">WCF Web Service Reference tool</span></span>](wcf-web-service-reference-guide.md)

<span data-ttu-id="c1446-106">WCF (Windows Communication Foundation) Web Service Reference は、Visual Studio に接続されているサービス プロバイダーです。[Visual Studio 2017 バージョン 15.5](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools) から導入されました。</span><span class="sxs-lookup"><span data-stu-id="c1446-106">The WCF (Windows Communication Foundation) Web Service Reference is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools).</span></span> <span data-ttu-id="c1446-107">このツールは現在のソリューションの Web サービスから、ネットワーク上の場所で、あるいは WSDL ファイルからメタデータを取得し、.NET Core と互換性のあるソース ファイルを生成し、Web サービス操作のアクセスに使用できるメソッドで WCF プロキシ クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="c1446-107">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[<span data-ttu-id="c1446-108">WCF dotnet-svcutil ツール</span><span class="sxs-lookup"><span data-stu-id="c1446-108">WCF dotnet-svcutil tool</span></span>](dotnet-svcutil-guide.md)

<span data-ttu-id="c1446-109">WCF (Windows Communication Foundation) dotnet-svcutil ツールは、ネットワーク上の場所で Web サービスから、あるいは WSDL ファイルからメタデータを取得し、.NET Core と互換性があるソース ファイルを生成して、Web サービス操作のアクセスに使用できるメソッドで WCF プロキシ クラスを定義する .NET Core CLI ツールです。</span><span class="sxs-lookup"><span data-stu-id="c1446-109">The WCF (Windows Communication Foundation) dotnet-svcutil tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span> <span data-ttu-id="c1446-110">**dotnet-svcutil** ツールは、Visual Studio 2017 v15.5 で最初に用意された Visual Studio 接続済みサービス プロバイダーである、[**WCF Web Service Reference**](/dotnet/core/additional-tools/wcf-web-service-reference-guide) に対する代わりのオプションです。</span><span class="sxs-lookup"><span data-stu-id="c1446-110">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](/dotnet/core/additional-tools/wcf-web-service-reference-guide) Visual Studio connected service provider which first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="c1446-111">.NET Core CLI ツールとしての **dotnet-svcutil** ツールは、Linux、macOS、および Windows 上で利用可能なクロスプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="c1446-111">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[<span data-ttu-id="c1446-112">XML シリアライザー ジェネレーター</span><span class="sxs-lookup"><span data-stu-id="c1446-112">XML Serializer Generator</span></span>](xml-serializer-generator.md)

<span data-ttu-id="c1446-113">.NET Framework の [Xml シリアライザー ジェネレーター (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) と同様に、[Microsoft.XmlSerializer.Generator NuGet パッケージ](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)は .NET Core および .NET Standard ライブラリのソリューションです。</span><span class="sxs-lookup"><span data-stu-id="c1446-113">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="c1446-114">アセンブリに含まれる型の XML シリアル化アセンブリを作成することで、<xref:System.Xml.Serialization.XmlSerializer> を使用してその型のオブジェクトをシリアル化または逆シリアル化するときの XML シリアル化の起動パフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="c1446-114">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>
---
title: "XML スキーマ定義ツールと XML シリアル化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 67451a30e5681718e5b9cdd07468ac5bf20322bc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="f1610-102">XML スキーマ定義ツールと XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="f1610-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="f1610-103">XML スキーマ定義ツール ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) は、Windows® Software Development Kit (SDK) の一部として、.NET Framework ツールと共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="f1610-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="f1610-104">このツールは、主に次の 2 つの目的を実現するためにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="f1610-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="f1610-105">特定の XML スキーマ定義言語 (XSD) スキーマに準拠する C# クラス ファイルまたは Visual Basic クラス ファイルの生成。</span><span class="sxs-lookup"><span data-stu-id="f1610-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="f1610-106">このツールは、XML スキーマを引数として受け取り、<xref:System.Xml.Serialization.XmlSerializer> を使用したシリアル化時にそのスキーマに準拠している多数のクラスを含むファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="f1610-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="f1610-107">このツールを使用して、特定のスキーマに準拠するクラスを生成する方法については、「[方法 : XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1610-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="f1610-108">.dll ファイルまたは .exe ファイルからの XML スキーマ ドキュメントの生成。</span><span class="sxs-lookup"><span data-stu-id="f1610-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="f1610-109">作成済み、または属性を使用して変更済みの一連のファイルのスキーマを確認するには、このツールに DLL または EXE を引数として渡し、その XML スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="f1610-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="f1610-110">このツールを使用して、一連のクラスから XML スキーマ ドキュメントを生成する方法については、「[方法 : XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1610-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="f1610-111">このツールおよびその他のツールの詳細については、「[ツール](../../../docs/framework/tools/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1610-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="f1610-112">ツールのオプションの詳細については、「[XML スキーマ定義ツール (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1610-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1610-113">参照</span><span class="sxs-lookup"><span data-stu-id="f1610-113">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="f1610-114">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="f1610-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="f1610-115">XML スキーマ定義ツール (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="f1610-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="f1610-116">方法 : オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="f1610-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="f1610-117">方法 : オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="f1610-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="f1610-118">方法 : XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する</span><span class="sxs-lookup"><span data-stu-id="f1610-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)  
 [<span data-ttu-id="f1610-119">.NET Framework での XML スキーマのバインディング サポート</span><span class="sxs-lookup"><span data-stu-id="f1610-119">XML Schema Binding Support in the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)

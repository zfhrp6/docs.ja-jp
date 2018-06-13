---
title: XML スキーマ定義ツールと XML シリアル化
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: d0fb8f9c411da570f8b2d01aa299e3521a417ead
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582486"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="3bcc9-102">XML スキーマ定義ツールと XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="3bcc9-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="3bcc9-103">XML スキーマ定義ツール ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) は、Windows® Software Development Kit (SDK) の一部として、.NET Framework ツールと共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="3bcc9-104">このツールは、主に次の 2 つの目的を実現するためにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="3bcc9-105">特定の XML スキーマ定義言語 (XSD) スキーマに準拠する C# クラス ファイルまたは Visual Basic クラス ファイルの生成。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="3bcc9-106">このツールは、XML スキーマを引数として受け取り、<xref:System.Xml.Serialization.XmlSerializer> を使用したシリアル化時にそのスキーマに準拠している多数のクラスを含むファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="3bcc9-107">このツールを使用して、特定のスキーマに準拠するクラスを生成する方法については、「[方法 : XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="3bcc9-108">.dll ファイルまたは .exe ファイルからの XML スキーマ ドキュメントの生成。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="3bcc9-109">作成済み、または属性を使用して変更済みの一連のファイルのスキーマを確認するには、このツールに DLL または EXE を引数として渡し、その XML スキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="3bcc9-110">このツールを使用して、一連のクラスから XML スキーマ ドキュメントを生成する方法については、「[方法 : XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="3bcc9-111">このツールおよびその他のツールの詳細については、「[ツール](../../../docs/framework/tools/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="3bcc9-112">ツールのオプションの詳細については、「[XML スキーマ定義ツール (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bcc9-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcc9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bcc9-113">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="3bcc9-114">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="3bcc9-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="3bcc9-115">XML スキーマ定義ツール (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="3bcc9-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="3bcc9-116">方法 : オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="3bcc9-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="3bcc9-117">方法 : オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="3bcc9-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="3bcc9-118">方法 : XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する</span><span class="sxs-lookup"><span data-stu-id="3bcc9-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)  
 [<span data-ttu-id="3bcc9-119">.NET Framework での XML スキーマのバインディング サポート</span><span class="sxs-lookup"><span data-stu-id="3bcc9-119">XML Schema Binding Support in the .NET Framework</span></span>](https://msdn.microsoft.com/library/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)

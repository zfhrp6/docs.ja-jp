---
title: XmlSerializer によるカスタム シリアル化順序
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b091d07ada0031013c935c5ab12b77ebedd6bcc3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="a8fb4-102">XmlSerializer によるカスタム シリアル化順序</span><span class="sxs-lookup"><span data-stu-id="a8fb4-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="a8fb4-103">サンプルのダウンロード</span><span class="sxs-lookup"><span data-stu-id="a8fb4-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="a8fb4-104">このサンプルでは、XML シリアル化で、シリアル化される要素および逆シリアル化される要素の順序を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8fb4-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="a8fb4-105">シリアル化の詳細については、ソース コード ファイルおよび build.proj ファイル内のコメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8fb4-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="a8fb4-106">コマンド プロンプトを使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="a8fb4-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="a8fb4-107">コマンド プロンプト ウィンドウを開き、サンプルの使用言語に対応するサブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="a8fb4-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="a8fb4-108">コマンド ラインで「**msbuild CustomOrder.sln**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a8fb4-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="a8fb4-109">Visual Studio を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="a8fb4-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="a8fb4-110">[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]を開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。</span><span class="sxs-lookup"><span data-stu-id="a8fb4-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="a8fb4-111">CustomOrder.sln のアイコンをダブルクリックして、このファイルを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="a8fb4-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="a8fb4-112">**[ビルド]** メニューで、**[ソリューションのビルド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a8fb4-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="a8fb4-113">サンプル アプリケーションは、既定の \bin ディレクトリまたは \bin\Debug ディレクトリにビルドされます。</span><span class="sxs-lookup"><span data-stu-id="a8fb4-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8fb4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8fb4-114">See Also</span></span>  
 [<span data-ttu-id="a8fb4-115">基本的なシリアル化</span><span class="sxs-lookup"><span data-stu-id="a8fb4-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="a8fb4-116">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="a8fb4-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="a8fb4-117">属性を使用した XML シリアル化の制御</span><span class="sxs-lookup"><span data-stu-id="a8fb4-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="a8fb4-118">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="a8fb4-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="a8fb4-119">シリアル化</span><span class="sxs-lookup"><span data-stu-id="a8fb4-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="a8fb4-120">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="a8fb4-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)

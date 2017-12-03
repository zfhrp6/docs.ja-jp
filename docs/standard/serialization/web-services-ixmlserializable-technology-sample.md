---
title: "Web サービス IXmlSerializable の技術サンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73ce34f101efc4f439b83e9a1ed69d286971486e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="44eb8-102">Web サービス IXmlSerializable の技術サンプル</span><span class="sxs-lookup"><span data-stu-id="44eb8-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="44eb8-103">サンプルのダウンロード</span><span class="sxs-lookup"><span data-stu-id="44eb8-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="44eb8-104">このサンプルでは、<xref:System.Xml.Serialization.IXmlSerializable> を使用して、ASP.NET Web サービスでカスタム型のシリアル化を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="44eb8-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="44eb8-105">Visual Studio を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="44eb8-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="44eb8-106">[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] を起動し、**[ファイル]** メニューの **[新しい Web サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44eb8-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="44eb8-107">**[新しい Web サイト]** ダイアログ ボックスの左ペインで、目的のプログラミング言語を選択し、右ペインの **[ASP.NET Web サービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44eb8-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="44eb8-108">Web サービスの名前として、「**IXmlSerializable**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="44eb8-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="44eb8-109">ソリューション エクスプローラー ウィンドウで、Service.asmx のアイコンを右クリックし、**[削除]** をクリックします。この手順を Service.asmx Codebehind ファイルに対して繰り返します。</span><span class="sxs-lookup"><span data-stu-id="44eb8-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="44eb8-110">プロジェクト ディレクトリを右クリックし、**[既存項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44eb8-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="44eb8-111">ダイアログ ボックスで、言語固有のディレクトリにある Service サブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="44eb8-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="44eb8-112">Service.asmx をクリックします。この手順を Service.asmx Codebehind ファイルに対して繰り返します。</span><span class="sxs-lookup"><span data-stu-id="44eb8-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="44eb8-113">[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]を開き、上記の手順 3. で作成した IXmlSerializable ディレクトリを含むディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="44eb8-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="44eb8-114">IXmlSerializable ディレクトリを右クリックし、**[共有とセキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44eb8-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="44eb8-115">[Web 共有] タブで、**[このフォルダーを共有する]** をクリックし、名前 IXmlSerializable など既定の設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="44eb8-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="44eb8-116">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44eb8-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="44eb8-117">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="44eb8-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="44eb8-118">Web ブラウザー ウィンドウを開き、アドレス バーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="44eb8-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="44eb8-119">「**http://localhost/IXmlSerializable/Service.asmx**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="44eb8-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44eb8-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="44eb8-120">See Also</span></span>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>

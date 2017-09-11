---
title: "ファイル名で指定されたファイルは有効な XML ファイルではありません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8b46b9d896f0dce401992e8a20e040b85091ba5d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="510cc-102">FileName で指定されたファイルは、正しい XML ファイルではありません</span><span class="sxs-lookup"><span data-stu-id="510cc-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="510cc-103">指定したファイル名は、正しい XML ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="510cc-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="510cc-104">XML ドキュメントの許可されている構造体とコンテンツを指定する場合、ドキュメント型定義 (DTD)、Microsoft XML-Data Reduced (XDR) スキーマ、または XML スキーマ定義言語 (XSD) スキーマを使用できます。</span><span class="sxs-lookup"><span data-stu-id="510cc-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="510cc-105">XSD スキーマは、XML 文法でを指定することをお勧めします[!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="510cc-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="510cc-106">Visual Studio の以前のバージョンにある **XML デザイナー** とは、型指定されたデータセットおよび XML スキーマのデザイナーのことです。</span><span class="sxs-lookup"><span data-stu-id="510cc-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="510cc-107">**XML デザイナー** は、XML スキーマ ファイルの作成と編集に今も使用できます。</span><span class="sxs-lookup"><span data-stu-id="510cc-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="510cc-108">ただし、 [!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)]、型指定されたデータセットを作成および編集デザイナーは、**データセット デザイナー**します。</span><span class="sxs-lookup"><span data-stu-id="510cc-108">However, in [!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="510cc-109">詳細については、次を参照してください。[の作成と型指定されたデータセットの編集](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets)します。</span><span class="sxs-lookup"><span data-stu-id="510cc-109">For more information, see [Creating and Editing Typed Datasets](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="510cc-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="510cc-110">To correct this error</span></span>  
  
-   <span data-ttu-id="510cc-111">正しいファイル名を指定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="510cc-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="510cc-112">確認する必要のある XML ファイルを **XML デザイナー**に読み込んで、指定したファイルに正しい XML が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="510cc-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="510cc-113">**[XML]** メニューで、 **[XML の整合性チェック]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="510cc-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="510cc-114">エラーは **[タスク一覧]**に表示されます。</span><span class="sxs-lookup"><span data-stu-id="510cc-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="510cc-115">XML ファイルに関連付けられた XML スキーマがある場合は、定義された構造体にその要素が出現し、個々の要素のコンテンツがスキーマで指定された宣言されたデータ型に準拠していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="510cc-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510cc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="510cc-116">See Also</span></span>  
 <span data-ttu-id="510cc-117"><xref:System.Xml></xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="510cc-117"><xref:System.Xml></span></span>   
<span data-ttu-id="510cc-118"> [方法: ファイル パスを解析する](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)</span><span class="sxs-lookup"><span data-stu-id="510cc-118"> [How to: Parse File Paths](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)</span></span>

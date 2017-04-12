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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2fa595ab411fdd300327db9e1fcca1e3156c7eed
ms.lasthandoff: 03/13/2017

---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>FileName で指定されたファイルは、正しい XML ファイルではありません
指定したファイル名は、正しい XML ファイルではありません。 XML ドキュメントの許可されている構造体とコンテンツを指定する場合、ドキュメント型定義 (DTD)、Microsoft XML-Data Reduced (XDR) スキーマ、または XML スキーマ定義言語 (XSD) スキーマを使用できます。 XSD スキーマは、XML 文法でを指定することをお勧めします[!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)]します。  
  
> [!NOTE]
>  Visual Studio の以前のバージョンにある **XML デザイナー** とは、型指定されたデータセットおよび XML スキーマのデザイナーのことです。 **XML デザイナー** は、XML スキーマ ファイルの作成と編集に今も使用できます。 ただし、 [!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)]、型指定されたデータセットを作成および編集デザイナーは、**データセット デザイナー**します。 詳細については、次を参照してください。[の作成と型指定されたデータセットの編集](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets)します。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   正しいファイル名を指定していることを確認します。  
  
-   確認する必要のある XML ファイルを **XML デザイナー**に読み込んで、指定したファイルに正しい XML が含まれていることを確認します。 **[XML]** メニューで、 **[XML の整合性チェック]**をクリックします。 エラーは **[タスク一覧]**に表示されます。  
  
-   XML ファイルに関連付けられた XML スキーマがある場合は、定義された構造体にその要素が出現し、個々の要素のコンテンツがスキーマで指定された宣言されたデータ型に準拠していることを確認します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml></xref:System.Xml>   
 [方法: ファイル パスを解析する](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

---
title: "My.Resources オブジェクト |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
dev_langs:
- VB
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6ad5bd4e33438256719b59cb0936cf6bc8525ab1
ms.lasthandoff: 03/13/2017

---
# <a name="myresources-object"></a>My.Resources オブジェクト
アプリケーションのリソースにアクセスするためには、プロパティとクラスを提供します。  
  
## <a name="remarks"></a>コメント  
 `My.Resources`オブジェクトがアプリケーションのリソースへのアクセスを提供しを使用すると動的にアプリケーションのリソースを取得します。 詳細については、次を参照してください。[を管理するアプリケーションのリソース (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)します。  
  
 `My.Resources`オブジェクトはグローバル リソースだけを公開します。 フォームに関連付けられているリソース ファイルへのアクセスは行いません。 フォームのフォーム リソースにアクセスする必要があります。 詳しくは、「[チュートリアル: Windows フォームのローカリゼーション](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)」をご覧ください。  
  
 アプリケーションのカルチャに固有のリソース ファイルにアクセスできる、`My.Resources`オブジェクトです。 既定では、`My.Resources`オブジェクトのカルチャに対応するリソース ファイルからリソースを検索、<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>プロパティ</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>。 ただし、この動作をオーバーライドし、リソースに使用する特定のカルチャを指定できます。 詳細については、次を参照してください。[デスクトップ アプリでのリソース](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)します。  
  
## <a name="properties"></a>プロパティ  
 プロパティ、`My.Resources`オブジェクトが、アプリケーションのリソースへの読み取り専用のアクセスを提供します。 追加またはリソースを削除するを使用して、**プロジェクト デザイナー**します。 詳細については、次を参照してください。[方法: リソース追加または削除](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)します。 使用して追加のリソースにアクセスすることができます、**プロジェクト デザイナー**を使用して`My.Resources.``resourceName`します。  
  
 追加またはでプロジェクトを選択してリソース ファイルを削除することも**ソリューション エクスプ ローラー**をクリックすると、**新しい項目の追加**または**既存項目の追加**から、**プロジェクト**メニュー。 使用して、この方法で追加のリソースにアクセスすることができます`My.Resources.``resourceFileName`.`resourceName`します。  
  
 各リソースには、名前、カテゴリ、および値、およびこれらのリソース設定で、リソースにアクセスするプロパティの表示方法を決定する、`My.Resources`オブジェクトです。 追加するリソースの**プロジェクト デザイナー**:  
  
-   名前、プロパティの名前を決定します。  
  
-   リソース データは、プロパティの値  
  
-   カテゴリは、プロパティの型を決定します。  
  
|カテゴリ|プロパティのデータ型|  
|---|---|  
|**文字列**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**イメージ**|<xref:System.Drawing.Bitmap></xref:System.Drawing.Bitmap>|  
|**アイコン**|<xref:System.Drawing.Icon></xref:System.Drawing.Icon>|  
|**オーディオ**|<xref:System.IO.UnmanagedMemoryStream></xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>クラスから派生する、<xref:System.IO.Stream>クラスなど、ストリームを受け取るメソッドを使用できるように、<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>メソッド</xref:Microsoft.VisualBasic.Devices.Audio.Play%2A></xref:System.IO.Stream></xref:System.IO.UnmanagedMemoryStream>。|  
|**ファイル**|-   [文字列](../../../visual-basic/language-reference/data-types/string-data-type.md)テキスト ファイルにします。<br />-<xref:System.Drawing.Bitmap>の画像ファイル</xref:System.Drawing.Bitmap>。<br />-<xref:System.Drawing.Icon>アイコン ファイル</xref:System.Drawing.Icon>。<br />-<xref:System.IO.UnmanagedMemoryStream>のサウンド ファイル</xref:System.IO.UnmanagedMemoryStream>。|  
|**その他**|デザイナーの情報によって判断**型**列です。|  
  
## <a name="classes"></a>クラス  
 `My.Resources`オブジェクトは各リソース ファイルを共有のプロパティを持つクラスとして公開します。 クラス名は、リソース ファイルの名前と同じです。 前のセクションで説明したように、リソース ファイル内のリソースは、クラスのプロパティとして公開されます。  
  
## <a name="example"></a>例  
 この例では、フォームのタイトルを設定するという名前の文字列リソース`Form1Title`アプリケーションのリソース ファイルにします。 例を実行するには、アプリケーションが必要という名前の文字列`Form1Title`リソース ファイルにします。 詳細については、次を参照してください。[方法: リソース追加または削除](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)します。  
  
 [!code-vb[VbVbalrMyResources&#1;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>例  
 この例では、フォームのアイコンを設定するという名前のアイコン`Form1Icon`アプリケーションのリソース ファイルに格納されています。 例を実行するには、アプリケーションが必要という名前のアイコン`Form1Icon`リソース ファイルにします。  
  
 [!code-vb[VbVbalrMyResources&#2;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>例  
 この例では、フォームの背景イメージを設定という名前のイメージ リソースを`Form1Background`がアプリケーションのリソース ファイル内にあります。 この例を実行するには、アプリケーションが必要という名前のイメージ リソース`Form1Background`リソース ファイルにします。  
  
 [!code-vb[VbVbalrMyResources&#3;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>例  
 この例は、名前付きオーディオ リソースとして格納されているサウンドを再生`Form1Greeting`アプリケーションのリソース ファイルにします。 例を実行するには、アプリケーションが必要というオーディオ リソース`Form1Greeting`リソース ファイルにします。 `My.Computer.Audio.Play`メソッドは、Windows フォーム アプリケーションでのみ使用します。  
  
 [!code-vb[VbVbalrMyResources&4;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>例  
 この例では、アプリケーションの文字列リソースのフランス語のカルチャのバージョンを取得します。 リソースが名前付き`Message`です。 カルチャを変更すること、`My.Resources`オブジェクトを使用して、 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>の例  
  
 この例を実行するには、アプリケーションが必要という名前の文字列`Message`でのリソース ファイル、およびアプリケーションが必要にあり用、そのリソース ファイルのフランス語のカルチャのバージョン。 詳細については、次を参照してください。[方法: リソース追加または削除](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)します。 アプリケーションには、リソース ファイルのフランス語のカルチャのバージョンがない場合、`My.Resource`オブジェクトは、既定のカルチャ リソース ファイルからリソースを取得します。  
  
 [!code-vb[VbVbalrMyResources&#10;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>関連項目  
 [方法: リソース追加または削除](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)   
 [アプリケーションのリソース (.NET) の管理](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)   
 [デスクトップ アプリでのリソース](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)   
 [チュートリアル: Windows フォームのローカリゼーション](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)

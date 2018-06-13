---
title: My.Resources オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 9fd23cb119ff9148a45d32ec70ccc4dad08ab876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604706"
---
# <a name="myresources-object"></a>My.Resources オブジェクト
アプリケーションのリソースにアクセスするには、プロパティとクラスを提供します。  
  
## <a name="remarks"></a>コメント  
 `My.Resources`オブジェクトがアプリケーションのリソースへのアクセスを提供および使用すると動的にアプリケーションのリソースを取得します。 詳細については、次を参照してください。[を管理するアプリケーションのリソース (.NET)](/visualstudio/ide/managing-application-resources-dotnet)です。  
  
 `My.Resources`オブジェクトはグローバル リソースのみを公開します。 フォームに関連付けられているリソース ファイルへのアクセスは提供されません。 フォームからフォーム リソースにアクセスする必要があります。  
  
 アプリケーションのカルチャに固有のリソース ファイルにアクセスすることができます、`My.Resources`オブジェクト。 既定では、`My.Resources`オブジェクト内のカルチャに一致するリソース ファイルからリソースを検索、<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>プロパティです。 ただし、この動作をオーバーライドし、リソースを使用する特定のカルチャを指定できます。 詳細については、「[デスクトップ アプリケーションのリソース](../../../framework/resources/index.md)」を参照してください。  
  
## <a name="properties"></a>プロパティ  
 プロパティ、`My.Resources`オブジェクトは、アプリケーションのリソースへの読み取り専用のアクセスを提供します。 追加またはリソースを削除するを使用して、**プロジェクト デザイナー**です。 によって追加されるリソースにアクセスすることができます、**プロジェクト デザイナー**を使用して`My.Resources.``resourceName`です。  
  
 追加またはでプロジェクトを選択してリソース ファイルを削除することができますも**ソリューション エクスプ ローラー**をクリックすると、**新しい項目の追加**または**既存項目の追加**から、 **プロジェクト**メニュー。 使用してこのような追加リソースにアクセスすることができます`My.Resources.``resourceFileName`.`resourceName`です。  
  
 各リソースの名前、カテゴリ、および、値があり、これらのリソース設定でのリソースにアクセスするプロパティの表示方法を決定、`My.Resources`オブジェクト。 追加するリソースの**プロジェクト デザイナー**:  
  
-   名前、プロパティの名前を決定します。  
  
-   リソース データは、プロパティの値  
  
-   カテゴリは、プロパティの型を決定します。  
  
|カテゴリ|プロパティのデータ型|  
|---|---|  
|**文字列**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**イメージ**|<xref:System.Drawing.Bitmap>|  
|**アイコン**|<xref:System.Drawing.Icon>|  
|**オーディオ**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>から派生したクラス、<xref:System.IO.Stream>など、ストリームを取るメソッドで使用できるように、クラス、<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>メソッドです。|  
|**ファイル**|-   [文字列](../../../visual-basic/language-reference/data-types/string-data-type.md)テキスト ファイルにします。<br />-   <xref:System.Drawing.Bitmap> イメージ ファイル。<br />-   <xref:System.Drawing.Icon> アイコン ファイルです。<br />-   <xref:System.IO.UnmanagedMemoryStream> 音声ファイル。|  
|**その他**|デザイナーの内の情報によって決まります**型**列です。|  
  
## <a name="classes"></a>クラス  
 `My.Resources`オブジェクトは、共有のプロパティを持つクラスとして各リソース ファイルを公開します。 クラス名は、リソース ファイルの名前と同じです。 前のセクションで説明した、リソース ファイル内のリソースが、クラスのプロパティとして公開されます。  
  
## <a name="example"></a>例  
 この例では、という名前の文字列リソースをフォームのタイトルを設定`Form1Title`アプリケーション リソース ファイルにします。 例が動作するには、アプリケーションが必要という名前の文字列`Form1Title`リソース ファイル。  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>例  
 この例は、という名前のアイコンをフォームのアイコンを設定`Form1Icon`アプリケーションのリソース ファイルに格納されています。 例が動作するには、アプリケーションが必要という名前のアイコン`Form1Icon`リソース ファイル。  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>例  
 この例では、という名前のイメージ リソースをフォームの背景イメージを設定`Form1Background`アプリケーションのリソース ファイルであります。 この例を実行するアプリケーションが必要という名前のイメージ リソース`Form1Background`リソース ファイル。  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>例  
 この例は、という名前のオーディオ リソースとして格納されているサウンドを再生`Form1Greeting`アプリケーションのリソース ファイルにします。 アプリケーションの例が機能するには、名前付きオーディオ リソースがある必要があります`Form1Greeting`リソース ファイル。 `My.Computer.Audio.Play`メソッドは、Windows フォーム アプリケーションでのみ使用します。  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>例  
 この例では、アプリケーションの文字列リソースのフランス語のカルチャのバージョンを取得します。 リソースが名前付き`Message`します。 カルチャを変更すること、`My.Resources`オブジェクトを使用して、この例では<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>します。  
  
 この例を実行するアプリケーションが必要という名前の文字列`Message`に、リソース ファイル、およびアプリケーションはがリソース ファイルで、あり用のフランス語のカルチャのバージョン。 アプリケーションには、リソース ファイルのフランス語のカルチャ バージョンがない場合、`My.Resource`オブジェクトは、既定のカルチャのリソース ファイルからリソースを取得します。  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション リソースの管理 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)  
 [デスクトップ アプリケーションのリソース](../../../framework/resources/index.md)  


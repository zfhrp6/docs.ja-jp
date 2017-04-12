---
title: "相互運用性 (Visual Basic) のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability
- interoperability, troubleshooting
- COM interop, troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: cbc37638ed5c57b94356c2d189f36b66202ceba5
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-interoperability-visual-basic"></a>相互運用性のトラブルシューティング (Visual Basic)
マネージ コードと COM の相互運用するときに、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]、次の一般的な問題が発生する可能性があります。  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a>相互運用マーシャ リング  
 いないデータ型を使用する必要がありますの一部では、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]です。 相互運用機能アセンブリ、COM オブジェクトに対する作業のほとんどを処理することはマネージ オブジェクトが COM に公開するときに使用されるデータ型を制御する必要があります。 たとえば、クラス ライブラリ内の構造体を指定する必要があります、`BStr`アンマネージ型 Visual Basic 6.0 およびそれ以前のバージョンで作成された COM オブジェクトに送信される文字列。 このような場合に使用することができます、<xref:System.Runtime.InteropServices.MarshalAsAttribute>アンマネージ型として公開するマネージ型が発生する属性</xref:System.Runtime.InteropServices.MarshalAsAttribute>。  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a>アンマネージ コードへの固定長文字列のエクスポート  
 Visual Basic 6.0 およびそれ以前のバージョンでは、文字列は null 終端文字なしバイトのシーケンスとして COM オブジェクトにエクスポートされます。 他の言語との互換性のため[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]文字列をエクスポートするときに終了文字が含まれています。 この非互換性に対処する最善の方法は、文字列の配列として、終了文字に関連付けられていないをエクスポートする`Byte`または`Char`です。  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a>継承階層のエクスポート  
 マネージ クラスが COM オブジェクトとして公開されるときに階層が平坦化します。 たとえば場合は、メンバーを持つ基本クラスを定義し、COM オブジェクトとして公開されている派生クラスで基本クラスを継承すると、COM オブジェクトに、派生クラスを使用するクライアントされません継承されたメンバーを使用すること。 基本クラスのメンバーは、基底クラスのインスタンスとしてのみ COM オブジェクトからアクセスできるし、基本クラスが COM オブジェクトとしても作成する場合にのみです。  
  
## <a name="overloaded-methods"></a>オーバーロードされたメソッド  
 オーバー ロードされたでメソッドを作成できますが、 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]COM でサポートされていません オーバー ロードされたメソッドを含むクラスが COM オブジェクトとして公開されているオーバー ロードされたメソッドの新しいメソッド名が生成されます。  
  
 たとえばの&2; つのオーバー ロードを持つクラス、`Synch`メソッドです。 新しいの生成されたメソッド名にすることが、クラスが COM オブジェクトとして公開されているときに`Synch`と`Synch_2`です。  
  
 名前を変更すると、COM オブジェクトのコンシューマー向けの&2; つの問題が発生することができます。  
  
1.  クライアントでは、生成されたメソッド名は予期しない可能性があります。  
  
2.  新しいオーバー ロードがクラスまたはその基本クラスに追加されたときに、COM オブジェクトとして公開するクラスで生成されたメソッド名を変更できます。 バージョン管理の問題がある可能性があります。  
  
 両方の問題を解決するために各メソッドに、COM オブジェクトとして公開されるオブジェクトを開発するときに、オーバー ロードを使用する代わりに、一意の名前を指定します。  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a>相互運用機能アセンブリを介して COM オブジェクトの使用  
 表す COM オブジェクトのマネージ コードに置き換わる場合とほとんど同じように相互運用機能アセンブリを使用するとします。 ただし、これらはのでラッパーと実際の COM オブジェクトは、相互運用機能アセンブリと標準のアセンブリを使用して違いです。 相違点には、クラス、およびパラメーターと戻り値のデータ型の公開が含まれます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a>両方のインターフェイスとして公開されるクラスとクラス  
 標準アセンブリのクラスとは異なり、COM クラスは、インターフェイスおよび COM クラスを表すクラスの両方との相互運用機能アセンブリで公開されます。 インターフェイスの名前は、COM クラスの場合と同じです。 相互運用機能のクラスの名前は元の COM クラスと同じですが、"Class"が追加の単語です。 たとえば、COM オブジェクトの相互運用機能アセンブリへの参照を含むプロジェクトがあるとします。 COM クラスの名前は場合`MyComClass`、IntelliSense やオブジェクト ブラウザーには、という名前のインターフェイスを表示する`MyComClass`という名前のクラスと`MyComClassClass`です。  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a>.NET Framework クラスのインスタンスを作成します。  
 インスタンスを作成する、一般に、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]クラスを使用して、`New`クラス名を含むステートメント。 相互運用機能アセンブリによって表される COM クラスは、1 つのケースを使用することができます、`New`ステートメント インターフェイスを使用します。 使用して COM クラスを使用している場合を除き、`Inherits`ステートメント、クラスと同様に、インターフェイスを使用することができます。 次のコードを作成する方法の例、 `Command` Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照を含むプロジェクト内のオブジェクト。  
  
 [!code-vb[VbVbalrInterop&#20;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 ただし、COM クラスは、派生クラスで、ベースとして使用されている場合は、次のコードのように、COM クラスを表す相互運用機能クラスを使用する必要があります。  
  
 [!code-vb[VbVbalrInterop #&21;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  相互運用機能アセンブリは、暗黙的に COM クラスを表すインターフェイスを実装します。 使用していけません、`Implements`これらのインターフェイスまたはエラーを実装するステートメントになります。  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a>パラメーターと戻り値のデータ型  
 相互運用機能アセンブリのメンバーは、標準のアセンブリのメンバーとは異なり、元のオブジェクトの宣言で使用されているとは異なるデータ型があります。 相互運用機能アセンブリは COM 型を互換性のある共通言語ランタイム型に暗黙的に変換しますが、両方の側で実行時エラーを回避するために使用されるデータ型に注意する必要があります。 たとえば、Visual Basic 6.0 以前のバージョンでは、型の値で作成された COM オブジェクトで`Integer`前提としています、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]同等型`Short`します。 使用する前に、インポートされたメンバーの特性を調べるオブジェクト ブラウザーを使用することをお勧めします。  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a>モジュール レベルの COM メソッド  
 使用して COM クラスのインスタンスを作成することでほとんどの COM オブジェクトが使用される、`New`キーワードと、オブジェクトのメソッドを呼び出しています。 この規則の例外は、COM オブジェクトを含む`AppObj`または`GlobalMultiUse`COM クラスです。 このようなクラスで、モジュール レベル メソッドのように[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]クラスです。 Visual Basic 6.0 とそれ以前のバージョンが暗黙的に作成このようなオブジェクトのインスタンスを最初にそれらのメソッドのいずれかを呼び出すことです。 たとえば、Visual Basic 6.0 で、参照を追加できます 3.6 DAO オブジェクト ライブラリを呼び出し、`DBEngine`インスタンスを作成せずメソッド。  
  
```  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]それらのメソッドを使用する前に常に COM オブジェクトのインスタンスを作成することが必要です。 これらのメソッドを使用する[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]、目的のクラスの変数を宣言し、新しいキーワードを使用して、オブジェクト変数にオブジェクトを割り当てます。 `Shared`ことを確認する場合に、キーワードを使用できるクラスの&1; つのインスタンスを作成します。  
  
 [!code-vb[VbVbalrInterop 第&23;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a>イベント ハンドラーで処理されないエラー  
 1 つの一般的な相互運用機能の問題には、COM オブジェクトによって生成されるイベントを処理するイベント ハンドラーでエラーが含まれています。 具体的にを使用してエラーをチェックする場合を除き、このようなエラーは無視されます`On Error`または`Try...Catch...Finally`ステートメントです。 たとえば、次の例からは、 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照を含むプロジェクトです。  
  
 [!code-vb[VbVbalrInterop #&24;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 この例では、予期したとおりにエラーが発生します。 ただし、なしの例と同じしようとすると、`Try...Catch...Finally`使用する場合と同様、ブロック、エラーは無視されます、`OnError Resume Next`ステートメントです。 エラー処理がなければ&0; による除算はサイレント モードで失敗します。 このようなエラーが処理されない例外エラーを発生しないことが COM オブジェクトからのイベントを処理するイベント ハンドラーで例外処理のいくつかの形式を使用することが重要です。  
  
### <a name="understanding-com-interop-errors"></a>COM 相互運用機能の問題を理解します。  
 エラー処理がない相互運用呼び出しは多くの場合、ほとんどの情報を提供するエラーを生成します。 可能であれば、構造化エラーが発生したときに、問題に関する詳細情報を提供する処理を使用します。 これはするアプリケーションをデバッグする場合に特に役立ちます。 例:  
  
 [!code-vb[VbVbalrInterop&#25;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 例外オブジェクトの内容を確認するには、エラーの説明、HRESULT、および COM エラーのソースなどの情報が表示されます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a>ActiveX コントロールに関する問題  
 Visual Basic 6.0 で使用するほとんどの ActiveX コントロールが扱う[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]難しくありません。 主な例外は、コンテナー コントロールまたはその他のコントロールを視覚的に格納しているコントロールです。 正しく動作しない古いコントロールの例をいくつか[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]は次のようになります。  
  
-   Microsoft フォーム 2.0 フレーム コントロール  
  
-   アップダウン コントロール、スピン コントロールとも呼ばれます  
  
-   Sheridan タブ コントロール  
  
 サポートされていない ActiveX コントロールに関する問題のいくつかの回避策のみがあります。 既存のコントロールを移行する[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]元のソース コードを所有している場合。 それ以外の場合、更新、ソフトウェア ベンダーに確認することができます。NET と互換性のあるバージョンの置換をコントロールには、ActiveX コントロールがサポートされていません。  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a>コントロールの ByRef の読み取り専用プロパティの引き渡し  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]渡すと場合があります"エラー 0x800A017F CTL_E_SETNOTSUPPORTED"などの COM エラーを発生させる`ReadOnly`として、一部の古い ActiveX コントロールのプロパティ`ByRef`他のプロシージャのパラメーターです。 Visual Basic 6.0 からプロシージャ呼び出しでは、エラーが発生せず、パラメーターとして扱われます値で渡すと同様です。 表示されるエラー メッセージ、[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]プロパティがないプロパティを変更しようとしていることを報告する COM オブジェクトは、`Set`プロシージャです。  
  
 呼び出されるプロシージャにアクセスできる場合を使用してこのエラーを回避できる、`ByVal`が受け取るパラメーターを宣言するキーワード`ReadOnly`プロパティです。 例:  
  
 [!code-vb[VbVbalrInterop #&26;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 呼び出されるプロシージャのソース コードへのアクセスがあるない場合は、呼び出し元のプロシージャの周囲に角かっこの追加のセットを追加することで値によって渡されるプロパティを強制できます。 たとえば、プロジェクトでは、Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照を含む、次のように使用します。  
  
 [!code-vb[VbVbalrInterop #&27;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a>相互運用機能を公開するアセンブリを展開します。  
 COM インターフェイスを公開するアセンブリを展開すると、特殊な課題が表示されます。 たとえば、別のアプリケーションは、同じ COM アセンブリを参照と、潜在的な問題が発生します。 新しいバージョンのアセンブリをインストールすると、別のアプリケーションは、アセンブリの旧バージョンを使用しても、このような状況が一般的です。 DLL を共有するアセンブリをアンインストールする場合することができ意図せずに使用できない他のアセンブリ。  
  
 この問題を回避するには、共有アセンブリをグローバル アセンブリ キャッシュ (GAC) にインストールして、コンポーネントのマージ モジュールを使用する必要があります。 GAC にアプリケーションをインストールできない場合は、これでバージョン固有のサブディレクトリで CommonFilesFolder にインストールしてください。  
  
 共有されていないアセンブリは、呼び出し元のアプリケーションと同じディレクトリにサイド バイ サイドで配置する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe (タイプ ライブラリ インポーター)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)   
 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)   
 [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [グローバル アセンブリ キャッシュ](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)

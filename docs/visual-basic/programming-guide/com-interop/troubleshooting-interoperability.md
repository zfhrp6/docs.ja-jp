---
title: 相互運用性のトラブルシューティング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
ms.openlocfilehash: 65005dbbe42f52b3159c8e595972dace3064f986
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-interoperability-visual-basic"></a>相互運用性のトラブルシューティング (Visual Basic)
マネージ コードと COM の相互運用するときに、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]、1 つ以上の次の一般的な問題が発生する可能性があります。  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> 相互運用マーシャ リング  
 れていないデータ型を使用する必要がありますの一部、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。 相互運用機能アセンブリ、COM オブジェクトの作業のほとんどを処理することはマネージ オブジェクトが COM に公開するときに使用されるデータ型を制御する必要があります。 たとえば、クラス ライブラリ内の構造を指定する必要があります、`BStr`アンマネージ型 Visual Basic 6.0 とそれ以前のバージョンで作成された COM オブジェクトに送信される文字列。 このような場合に使用することができます、<xref:System.Runtime.InteropServices.MarshalAsAttribute>アンマネージ型として公開するマネージ型が発生する属性。  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> アンマネージ コードへの固定長文字列のエクスポート  
 Visual Basic 6.0 とそれ以前のバージョンでは、文字列は、終端の null 文字を使用せずにバイトのシーケンスとして COM オブジェクトにエクスポートされます。 他の言語と互換性のため、Visual Basic .NET には、文字列をエクスポートするときに終了文字が含まれます。 この非互換性に対処する最善の方法では、文字列の配列として、終了文字がないをエクスポート`Byte`または`Char`です。  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> 継承階層のエクスポート  
 マネージ クラスが COM オブジェクトとして公開されるときに階層が平坦化します。 など、メンバーを持つ基本クラスを定義し、COM オブジェクトとして公開されている派生クラスで基底クラスを継承する場合、COM オブジェクトで、派生クラスを使用するクライアントされませんを継承されたメンバーを使用できません。 基本クラスのメンバーは、基底クラスのインスタンスとしてのみ COM オブジェクトからアクセスできるし、基本クラスが COM オブジェクトとして作成も場合のみです。  
  
## <a name="overloaded-methods"></a>オーバーロードされたメソッド  
 COM でサポートされていないオーバー ロードされたメソッドは、Visual Basic を使用して作成できますが、 オーバー ロードされたメソッドを含むクラスは、COM オブジェクトとして公開される、ときに、オーバー ロードされたメソッドの新しいメソッド名が生成されます。  
  
 たとえばの 2 つのオーバー ロードを持つクラスである、`Synch`メソッドです。 クラスが COM オブジェクトとして公開されている新しい生成されたメソッド名こと`Synch`と`Synch_2`です。  
  
 名前を変更すると、COM オブジェクトのコンシューマーの 2 つの問題が発生ことができます。  
  
1.  クライアントでは、生成されたメソッド名が予期しない可能性があります。  
  
2.  新しいオーバー ロードがクラスまたはその基本クラスに追加されたときに、COM オブジェクトとして公開されているクラスで生成されたメソッド名を変更できます。 これにより、バージョン管理の問題が発生することができます。  
  
 両方の問題を解決するには、各メソッドに、COM オブジェクトとして公開されるオブジェクトを開発するときに、オーバー ロードを使用する代わりに、一意の名前を指定します。  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> 相互運用機能アセンブリを介して COM オブジェクトの使用  
 相互運用機能アセンブリを使用して、それらが表す COM オブジェクトに置き換わるマネージ コードが場合とほとんど同じようにします。 ただし、ラッパーや実際の COM オブジェクトは、ためには、相互運用機能アセンブリと標準のアセンブリを使用して違いです。 相違点には、クラス、およびパラメーターと戻り値のデータ型の露出が含まれます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> 両方のインターフェイスとして公開されるクラスとクラス  
 標準のアセンブリのクラスとは異なり、COM クラスは、COM クラスを表すクラスとインターフェイスの両方と相互運用機能アセンブリで公開されます。 インターフェイスの名前は、COM クラスのものと同じです。 相互運用機能のクラスの名前は、元の COM クラスのものと同じですが、"Class"が追加の単語でします。 たとえば、COM オブジェクトの相互運用機能アセンブリへの参照とプロジェクトがあるとします。 COM クラスの名前は場合`MyComClass`、IntelliSense やオブジェクト ブラウザーには、という名前のインターフェイスを表示する`MyComClass`という名前のクラスと`MyComClassClass`です。  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> .NET Framework クラスのインスタンスを作成します。  
 インスタンスを作成する、一般に、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスを使用して、`New`ステートメントをクラス名でします。 相互運用機能アセンブリによって表される COM クラスが 1 つのケースが使用することができます、`New`ステートメント インターフェイスを使用します。 クラスを COM を使用している場合を除き、`Inherits`ステートメントでは、クラスと同様に、インターフェイスを使用することができます。 次のコードを作成する方法を示しています、`Command`を持つ、Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照をプロジェクト内のオブジェクト。  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 ただし、COM クラスは、派生クラスで、ベースとして使用されている場合は、次のコードのように、COM クラスを表す相互運用機能のクラスを使用する必要があります。  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  相互運用機能アセンブリは、暗黙的に COM クラスを表すインターフェイスを実装します。 使用するべきされません、`Implements`これらのインターフェイスまたはエラーを実装するステートメントが発生します。  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> パラメーターと戻り値のデータ型  
 相互運用機能アセンブリのメンバーは、標準のアセンブリのメンバーとは異なり、元のオブジェクトの宣言で使用されるものとは異なるデータ型があります。 相互運用機能アセンブリは COM 型を互換性のある共通言語ランタイムの型に暗黙的に変換しますが、両方の側で実行時エラーを回避するために使用されるデータ型に注意を払う必要があります。 たとえば、Visual Basic 6.0 と以前のバージョンでは、型の値で作成された COM オブジェクトで`Integer`前提としています、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]同等の型、`Short`です。 使用する前に、インポートされたメンバーの特性を調べるオブジェクト ブラウザーを使用することをお勧めします。  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> モジュール レベルの COM メソッド  
 ほとんどの COM オブジェクトが COM を使用するクラスのインスタンスを作成することで使用される、`New`キーワードと、オブジェクトのメソッドを呼び出します。 このルールに 1 つの例外とは、COM オブジェクトを含む`AppObj`または`GlobalMultiUse`COM クラスです。 このようなクラスには、モジュール レベルの Visual Basic .NET クラス メソッドに似ています。 Visual Basic 6.0 とそれ以前のバージョンが暗黙的に作成のようなオブジェクトのインスタンスを最初にそれらのメソッドのいずれかを呼び出すことです。 たとえば、Visual Basic 6.0 で追加できます DAO 3.6 オブジェクト ライブラリおよび呼び出しへの参照、`DBEngine`インスタンスを作成せずメソッド。  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET では、そのメソッドを使用する前に常に COM オブジェクトのインスタンスを作成することが必要です。 これらのメソッドを使用して、Visual Basic を希望のクラスの変数を宣言し、新しいキーワードを使用して、オブジェクト変数にオブジェクトを割り当てます。 `Shared`ことを確認するときに、キーワードを使用できるクラスの 1 つのインスタンスを作成します。  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> イベント ハンドラーで処理されないエラー  
 1 つの一般的な相互運用の問題には、COM オブジェクトによって生成されるイベントを処理するイベント ハンドラーでエラーが含まれます。 具体的を使用してエラーをチェックする場合を除き、このようなエラーは無視されます`On Error`または`Try...Catch...Finally`ステートメントです。 たとえば、次の例は、Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照を含む Visual Basic .NET プロジェクトです。  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 この例では、期待どおりにエラーが発生します。 ただし、せず同じ例を実行する場合、`Try...Catch...Finally`使用する場合と同様、ブロック、エラーは無視されます、`OnError Resume Next`ステートメントです。 エラー処理がなければ 0 による除算はサイレント モードで失敗します。 このようなエラーは、ハンドルされない例外エラーを発生させることはありません、それが COM オブジェクトからのイベントを処理するイベント ハンドラーでの例外処理のいくつかの形式を使用することが重要です。  
  
### <a name="understanding-com-interop-errors"></a>COM 相互運用の問題を理解します。  
 エラー処理がない相互運用呼び出しで生成されるエラー情報を過不足なくを提供します。 可能な限り、構造化エラーが発生したときに、問題に関する詳細情報を提供する処理を使用します。 これはれるアプリケーションをデバッグするときに特に役立ちます。 例えば:  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 例外オブジェクトの内容を確認するには、エラーの説明、HRESULT、および COM エラーのソースなどの情報が表示されます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> ActiveX コントロールに関する問題  
 Visual Basic 6.0 で動作するほとんどの ActiveX コントロールは、Visual Basic .NET で問題なく動作します。 主な例外は、コンテナーのコントロール、またはその他のコントロールを視覚的に格納しているコントロールです。 Visual Studio で正常に動作しない古いコントロールの例をいくつかは次のとおりです。  
  
-   Microsoft フォーム 2.0 フレーム コントロール  
  
-   アップダウン コントロール、スピン コントロールとも呼ばれます  
  
-   Sheridan タブ コントロール  
  
 サポートされていない ActiveX コントロールの問題のいくつかの回避策のみがあります。 元のソース コードを所有している場合は、Visual Studio に既存のコントロールを移行できます。 それ以外の場合、更新、ソフトウェア ベンダーに確認することができます。置換するコントロールの NET と互換性のあるバージョンには、ActiveX コントロールがサポートされていません。  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> コントロールの ByRef の読み取り専用プロパティの引き渡し  
 Visual Basic .NET 場合がありますを発生させます"エラー 0x800A017F CTL_E_SETNOTSUPPORTED"などの COM エラーを渡す場合`ReadOnly`として、一部の古い ActiveX コントロールのプロパティ`ByRef`他のプロシージャのパラメーターです。 Visual Basic 6.0 からプロシージャ呼び出しでは、エラーは発生せず、パラメーターとして扱われます値で渡すと同様です。 Visual Basic .NET のエラー メッセージは、プロパティを持たないプロパティを変更しようとしていることを示す`Set`プロシージャです。  
  
 呼び出されるプロシージャにアクセスできる場合を使用してこのエラーを防ぐことができます、`ByVal`を受け取るパラメーターを宣言するキーワード`ReadOnly`プロパティです。 例えば:  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 呼び出されるプロシージャのソース コードへのアクセスがない、余分な呼び出し元のプロシージャの前後にかっこのセットを追加することで値によって渡されるプロパティを強制することができます。 たとえば、プロジェクトでは、Microsoft ActiveX データ オブジェクト 2.8 ライブラリ COM オブジェクトへの参照を含む、次のように使用します。  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> 相互運用機能を公開するアセンブリを展開します。  
 COM インターフェイスを公開するアセンブリの展開の課題がいくつか一意です。 たとえば、別のアプリケーションは、同じ COM アセンブリを参照と、潜在的な問題が発生します。 アセンブリの新しいバージョンがインストールされているし、別のアプリケーションがまだ古いバージョンのアセンブリを使用して、このような状況が一般的です。 場合は、DLL を共有するアセンブリをアンインストールすると、することができます意図せずに使用できなくなったを他のアセンブリ。  
  
 この問題を回避するのには、共有アセンブリをグローバル アセンブリ キャッシュ (GAC) にインストールして、コンポーネントのマージ モジュールを使用してください。 GAC にアプリケーションをインストールできない場合は、これでバージョンに固有のサブディレクトリに CommonFilesFolder にインストールしてください。  
  
 共有されていないアセンブリは、呼び出し元のアプリケーションを使用してディレクトリにサイド バイ サイドで配置する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [チュートリアル : COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [グローバル アセンブリ キャッシュ](../../../framework/app-domains/gac.md)

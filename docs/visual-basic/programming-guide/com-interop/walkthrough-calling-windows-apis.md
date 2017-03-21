---
title: "チュートリアル: Windows Api (Visual Basic) の呼び出し |Microsoft ドキュメント"
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
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls, walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement, declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
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
ms.openlocfilehash: 5001ccebb0a5b8cadd4e856342601506cf1d033f
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>チュートリアル: Windows API の呼び出し (Visual Basic)
Windows Api は、Windows オペレーティング システムの一部であるダイナミック リンク ライブラリ (Dll) です。 それらを使用して、独自の同等のプロシージャの作成が困難になる場合は、タスクを実行します。 たとえば、という名前の関数は、Windows`FlashWindowEx`により、アプリケーションのタイトル バーを薄いおよび濃い網掛けが交互に行うためです。  
  
 コード内の Windows Api を使用する利点は、既に書き込まれている便利な関数が多数用意し、使用するには、待機しているが含まれているために、開発時間を節約することです。 欠点は、Windows Api は問題が生じた場合やェロェノェを処理できないことがあります。  
  
 Windows Api では、相互運用性の特別なカテゴリを表します。 Windows Api では、マネージ コードを使用しないでください、組み込みライブラリを入力し、Visual Studio で使用されるものとは異なるデータ型を使用する必要はありません。 これらの相違点は、Windows Api が COM オブジェクト、Windows Api との相互運用ではないため、および[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]はプラットフォームを使用して実行呼び出すには、pinvoke です。 プラットフォーム呼び出しはマネージ Dll に実装されているアンマネージ関数を呼び出すコードを有効にするサービスです。 詳細については、次を参照してください。[アンマネージ DLL 関数の処理](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045)します。 PInvoke を使用することができます[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を使用して、`Declare`ステートメントまたは適用する、`DllImport`属性を空のプロシージャです。  
  
 Windows API の呼び出しの重要な部分のされた[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、過去のプログラミングしますが、することはまれで必要な[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]です。 可能であればからマネージ コードを使用する必要があります、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] Windows API の呼び出しではなく、タスクを実行します。 このチュートリアルは、使用する必要のある状況についての情報を Windows Api が必要です。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="api-calls-using-declare"></a>使用して、API 呼び出しを宣言します。  
 Windows Api を呼び出す最も一般的な方法を使用して、`Declare`ステートメントです。  
  
#### <a name="to-declare-a-dll-procedure"></a>DLL のプロシージャを宣言するには  
  
1.  呼び出すには、必要な関数とその引数、引数の型の名前を特定し、値、だけでなく、名前、およびそれを含んでいる DLL の場所を返します。  
  
    > [!NOTE]
    >  Windows Api についての詳細については、プラットフォーム SDK の Windows API で Win32 SDK ドキュメントを参照してください。 Windows Api を使用する定数についての詳細については、Windows.h、Platform SDK に含まれているなどのヘッダー ファイルを調べてください。  
  
2.  クリックして新しい Windows アプリケーション プロジェクトを開きます**新規**上、**ファイル**] メニューの [クリックして**プロジェクト**します。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  選択**Windows アプリケーション**の一覧から[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクト テンプレートです。 新しいプロジェクトが表示されます。  
  
4.  次の追加`Declare`クラスまたは DLL を使用するモジュールのいずれかの機能します。  
  
     [!code-vb[VbVbalrInterop&#9;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>部分、Declare ステートメント  
 `Declare`ステートメントには、次の要素が含まれています。  
  
#### <a name="auto-modifier"></a>Auto 修飾子  
 `Auto`修飾子が共通言語ランタイムの規則 (またはエイリアス名を指定する場合) に従って、メソッド名に基づく文字列に変換するようランタイムに指示します。  
  
#### <a name="lib-and-alias-keywords"></a>Lib とエイリアスのキーワード  
 名前の次の`Function`キーワードは、インポートされた関数にアクセスするプログラムで使用される名前です。 を呼び出す関数の実際の名前と同じことができますか、任意の有効なプロシージャの名前と、採用を使用する、`Alias`キーワードを呼び出している関数の実際の名前を指定します。  
  
 指定の`Lib`キーワードを呼び出している関数を含んでいる DLL の場所と名前。 Windows システム ディレクトリ内にあるファイルのパスを指定する必要はありません。  
  
 使用して、`Alias`を呼び出している関数の名前が有効な場合は、キーワード[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャ名、または、アプリケーションでは、その他の項目の名前と競合します。 `Alias`呼び出される関数の本当の名前を示します。  
  
#### <a name="argument-and-data-type-declarations"></a>引数とデータ型の宣言  
 引数とそのデータ型を宣言します。 この部分は、Windows で使用されるデータ型は、Visual Studio のデータ型に対応していないために、困難な場合ことができます。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]この自動化は多くの作業を互換性のあるデータ型と呼ばれるプロセスに引数を変換する*マーシャ リング*します。 使用して引数をマーシャ リングする方法を明示的に制御できる、<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性で定義されている、<xref:System.Runtime.InteropServices>名前空間</xref:System.Runtime.InteropServices></xref:System.Runtime.InteropServices.MarshalAsAttribute>。  
  
> [!NOTE]
>  以前のバージョンの[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]パラメーターを宣言することができる`As Any`、つまり、すべてのデータのデータ型を使用できます。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]すべての特定のデータ型を使用することが必要です。`Declare`ステートメントです。  
  
#### <a name="windows-api-constants"></a>Windows API の定数  
 いくつかの引数は、定数の組み合わせです。 たとえば、`MessageBox`このチュートリアルで示すように API と呼ばれる整数の引数を受け取る`Typ`メッセージ ボックスを表示する方法を制御します。 確認するには、これらの定数の数値を指定できます、 `#define` WinUser.h ファイル内のステートメントです。 数値の値は、電卓を使用してそれらを追加し、10 進数に変換するために一般的に&16; 進数で表示されます。 例では、感嘆符スタイルの定数を結合する場合の`MB_ICONEXCLAMATION`0x00000030 し、はい/スタイルなし`MB_YESNO`0x00000004、番号を追加し、10 進数、0x00000034 または 52 の結果を取得します。 これらの値をアプリケーションで定数として宣言し、それらを結合することをお勧め&10; 進数の結果を直接使用できますを使用して、`Or`演算子。  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Windows API の呼び出しの定数を宣言するには  
  
1.  Windows 関数の呼び出しと、ドキュメントを参照してください。 使用されている定数の名前とこれらの定数の数値を含む .h ファイルの名前を決定します。  
  
2.  メモ帳などのテキスト エディターを使用して、ヘッダー (.h) ファイルの内容を表示しを使用している定数に関連付けられている値を検索します。 たとえば、 `MessageBox` API は、定数を使用して`MB_ICONQUESTION`メッセージ ボックスに疑問符 () を表示します。 定義を`MB_ICONQUESTION`WinUser.h にあり、次のように表示されます。  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  それと同等の追加`Const`ステートメントをクラスまたはモジュールをこれらの定数をアプリケーションで使用できるようにします。 例:  
  
     [!code-vb[VbVbalrInterop&#11;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>DLL のプロシージャを呼び出す  
  
1.  という名前のボタンを追加`Button1`の起動時に、プロジェクトの形式し、すると、そのコードを表示する をダブルクリックします。 ボタンのイベント ハンドラーが表示されます。  
  
2.  コードを追加して、`Click`プロシージャを呼び出すし、適切な引数を提供する、追加したボタンのイベント ハンドラー。  
  
     [!code-vb[VbVbalrInterop&#12;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  F5 キーを押して、プロジェクトを実行します。 両方で、メッセージ ボックスが表示**はい**と**いいえ**返信ボタン。 いずれかをクリックします。  
  
#### <a name="data-marshaling"></a>データ マーシャ リング  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動的に変換パラメーターと Windows API の呼び出しの戻り値のデータ型使える、 `MarshalAs` API のものと想定するアンマネージ データ型を明示的に指定する属性です。 相互運用マーシャ リングの詳細については、次を参照してください。[相互運用マーシャ リング](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)します。  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Declare と MarshalAs API 呼び出しで使用するには  
  
1.  データ型を引数、呼び出そうと関数の名前を特定し、値を返します。  
  
2.  アクセスを簡略化する、`MarshalAs`属性は、追加、`Imports`ステートメントをクラスまたは次の例のように、モジュールに対するコードの上部にします。  
  
     [!code-vb[VbVbalrInterop&#13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  クラスまたはモジュールを使用しているし、適用、インポートされた関数に対する関数プロトタイプを追加、`MarshalAs`属性をパラメーターまたは戻り値。 次の例では、型が必要ですが、API 呼び出しで`void*`としてマーシャ リング`AsAny`:  
  
     [!code-vb[VbVbalrInterop&#14;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>DllImport を使用する API 呼び出し  
 `DllImport`属性は、タイプ ライブラリを持たない Dll で関数を呼び出す&2; 番目の方法を提供します。 `DllImport`使用するとほぼ同じですが、`Declare`ステートメントが関数を呼び出す方法より詳細に制御を提供します。  
  
 使用する`DllImport`ほとんどの Windows API を使用、呼び出しは、共有を参照する限りを呼び出します (とも呼ばれる*静的*) メソッドです。 クラスのインスタンスを必要とするメソッドを使用することはできません。 異なり`Declare`ステートメント、`DllImport`呼び出しを使用できない、`MarshalAs`属性です。  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>DllImport 属性を使用して Windows API を呼び出す  
  
1.  クリックして新しい Windows アプリケーション プロジェクトを開きます**新規**上、**ファイル**] メニューの [クリックして**プロジェクト**します。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  選択**Windows アプリケーション**の一覧から[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクト テンプレートです。 新しいプロジェクトが表示されます。  
  
3.  という名前のボタンを追加`Button2`スタートアップ フォームにします。  
  
4.  ダブルクリックして`Button2`フォームのコード ビューを開きます。  
  
5.  アクセスを簡略化する`DllImport`、追加、`Imports`ステートメントをスタートアップ フォーム クラスのコードの上部にします。  
  
     [!code-vb[VbVbalrInterop&#13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  この空の関数を宣言、`End Class`フォーム、および関数の名前に対する`MoveFile`します。  
  
7.  適用、`Public`と`Shared`関数宣言とパラメーターを設定する修飾子`MoveFile`Windows API 関数を使用して、引数に基づいた。  
  
     [!code-vb[VbVbalrInterop&#16;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     関数は、任意の有効なプロシージャ名前を設定できます。`DllImport`属性は、DLL の名前を指定します。 パラメーターのマーシャ リングの相互運用性も処理やデータに類似する Visual Studio のデータ型を選択できるように、戻り値の型 API によって使用されるあります。  
  
8.  適用、`DllImport`属性を空の関数にします。 最初のパラメーターは、呼び出し先関数を含んでいる DLL の場所と名前です。 Windows システム ディレクトリ内にあるファイルのパスを指定する必要はありません。 2 番目のパラメーターは、Windows API の関数の名前を指定する名前付き引数です。 この例では、`DllImport`属性への呼び出しを強制する`MoveFile`に転送される`MoveFileW`KERNEL32 にします。DLL です。 `MoveFileW`メソッドは、パスからファイルをコピー`src`パスに`dst`します。  
  
     [!code-vb[VbVbalrInterop&17;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. コードを追加して、`Button2_Click`イベント ハンドラー関数を呼び出します。  
  
     [!code-vb[VbVbalrInterop&#18;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Test.txt という名前のファイルを作成し、ハード ドライブ上の C:\Tmp ディレクトリに配置します。 必要な場合は、Tmp ディレクトリを作成します。  
  
11. F5 キーを押してアプリケーションを起動します。 メイン フォームが表示されます。  
  
12. クリックして**Button2**します。 ファイルを移動できる場合は、「ファイルが正常に移動されました」メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.DllImportAttribute></xref:System.Runtime.InteropServices.DllImportAttribute>   
 <xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [自動](../../../visual-basic/language-reference/modifiers/auto.md)   
 [エイリアス](../../../visual-basic/language-reference/statements/alias-clause.md)   
 [COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md)   
 [マネージ コードでのプロトタイプの作成](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d)   
 [コールバック メソッドとしてデリゲートのマーシャ リング](http://msdn.microsoft.com/library/6ddd7866-9804-4571-84de-83f5cc017a5a)

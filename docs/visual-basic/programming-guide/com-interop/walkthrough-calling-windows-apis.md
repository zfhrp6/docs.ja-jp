---
title: "Walkthrough: Calling Windows APIs (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DLLs, calling"
  - "Windows API, walkthroughs"
  - "platform invoke, walkthroughs"
  - "API calls, walkthroughs [Visual Basic]"
  - "Windows API, calling"
  - "walkthroughs [Visual Basic], API calls"
  - "DllImport attribute, calling Windows API"
  - "Declare statement, declaring DLL functions"
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Walkthrough: Calling Windows APIs (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Windows API は、Windows オペレーティング システムの一部であるダイナミック リンク ライブラリ \(DLL: Dynamic Link Library\) です。  同等のプロシージャを独自に作成するのが困難なときに、Windows API を利用してタスクを実行します。  たとえば、Windows には `FlashWindowEx` という名前の関数があります。この関数を使用すると、アプリケーションのタイトル バーを明るい網かけと暗い網かけに交互に変化させることができます。  
  
 コードで Windows API を使用する利点は、開発時間を短縮できることです。Windows API には、作成済みの、すぐに利用できる便利な関数が数多く用意されているため、開発時間を短縮できます。  Windows API の短所としては、操作が難しい場合があることや、適切に動作しないときに修正できない場合があることが挙げられます。  
  
 Windows API は、相互運用性の特別なカテゴリを表します。  Windows API ではマネージ コードを使用せず、タイプ ライブラリが組み込まれていません。また、Visual Studio で使用されるデータ型とは異なるデータ型を使用します。  このような相違点、および Windows API は COM オブジェクトではないという理由により、Windows API と [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] の相互運用は、PInvoke \(プラットフォーム呼び出し\) を使用して実行されます。  プラットフォーム呼び出しは、DLL に実装されたアンマネージ関数をマネージ コードが呼び出すことができるサービスです。  詳細については、「[アンマネージ DLL 関数の処理](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)」を参照してください。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で PInvoke を使用するには、`Declare` ステートメントを使用するか、または `DllImport` 属性を空のプロシージャに適用します。  
  
 過去において Windows API 呼び出しは [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プログラミングの重要な部分を占めていましたが、[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] ではほとんど必要がなくなりました。  Windows API 呼び出しを使用する代わりに、できる限り [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] からマネージ コードを使用してタスクを実行する必要があります。  このチュートリアルでは、Windows API を使用する必要のある状況についての情報を提供します。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
## Declare による API 呼び出し  
 Windows API を呼び出す最も一般的な方法は、`Declare` ステートメントを使用する方法です。  
  
#### DLL プロシージャを宣言するには  
  
1.  呼び出しの対象となる関数の名前、引数、引数の型、戻り値、およびその関数を含む DLL の名前と場所を確認します。  
  
    > [!NOTE]
    >  Windows API の詳細については、プラットフォーム SDK の「Windows API」で、Win32 SDK に関する記述を参照してください。  Windows API で使用される定数の詳細については、プラットフォーム SDK に組み込まれている Windows.h などのヘッダー ファイルを参照してください。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をクリックし、**\[プロジェクト\]** をクリックして、新規の Windows アプリケーション プロジェクトを開きます。  **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
3.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プロジェクト テンプレートの一覧の **\[Windows アプリケーション\]** を選択します。  新しいプロジェクトが表示されます。  
  
4.  次の `Declare` 関数を、DLL を使用するクラスまたはモジュールに追加します。  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### Declare ステートメントの構成要素  
 `Declare` ステートメントは次の要素で構成されます。  
  
#### Auto 修飾子  
 `Auto` 修飾子は、共通言語ランタイムの実行時規則に従い、メソッド名またはエイリアス名 \(指定されている場合\) に基づいて、文字列を変換するようにランタイムに指示します。  
  
#### Lib キーワードと Alias キーワード  
 `Function` キーワードに続く名前は、インポートした関数にアクセスするためにプログラムで使用される名前です。  この名前には、呼び出しの対象となる関数の実際の名前を使用できます。また、任意の有効なプロシージャ名を使用してから、`Alias` キーワードを使用して呼び出しの対象となる関数の実際の名前を指定することもできます。  
  
 `Lib` キーワードは、呼び出しの対象となる関数を含む DLL の名前と場所の前に指定します。  Windows システム ディレクトリに格納されたファイルのパスを指定する必要はありません。  
  
 呼び出しの対象となる関数の名前が、有効な [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プロシージャ名でない場合、またはアプリケーション内の他の項目の名前と競合する場合は、`Alias` キーワードを使用します。  `Alias` は、呼び出される関数の実際の名前を示します。  
  
#### 引数とデータ型の宣言  
 引数とそのデータ型を宣言します。  この部分は、Windows が使用するデータ型が Visual Studio のデータ型に対応していないため、難しい部分です。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、*マーシャリング*と呼ばれるプロセスで、引数が互換性のあるデータ型に変換されます。  <xref:System.Runtime.InteropServices> 名前空間で定義されている <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用することによって、引数がマーシャリングされる方法を明示的に制御できます。  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の以前のバージョンでは、どのデータ型のデータでも使用可能にするパラメーター `As Any` を宣言できました。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、すべての `Declare` ステートメントに特定のデータ型を使用する必要があります。  
  
#### Windows API の定数  
 一部の引数は定数の組み合わせです。  たとえば、このチュートリアルで示す `MessageBox` API は、メッセージ ボックスの表示方法を制御する `Typ` と呼ばれる整数の引数を受け取ります。  これらの定数の数値を確認するには、WinUser.h ファイル内の `#define` ステートメントを調べます。  数値は通常 16 進数で示されるため、数値を加算したり 10 進数に変換したりする場合は、電卓を使用することをお勧めします。  たとえば、感嘆符スタイルの定数 `MB_ICONEXCLAMATION` 0x00000030 と Yes\/No スタイルの定数 `MB_YESNO` 0x00000004 を組み合わせる場合は、数値を加算して、0x00000034 \(10 進数では 52\) の結果を得ることができます。  10 進数の結果を直接使用することもできますが、アプリケーション内でこれらの値を定数として宣言し、`Or` 演算子を使用して組み合わせることをお勧めします。  
  
###### Windows API 呼び出しの定数を宣言するには  
  
1.  呼び出す Windows 関数のマニュアルを参照してください。  使用する定数の名前と、これらの定数に対応する数値を含む .h ファイルの名前を決定します。  
  
2.  メモ帳などのテキスト エディターを使用して、ヘッダー \(.h\) ファイルの内容を表示し、使用する定数に関連付けられた値を探します。  たとえば、`MessageBox` API は、定数 `MB_ICONQUESTION` を使用して、メッセージ ボックスに疑問符を表示します。  `MB_ICONQUESTION` の定義は WinUser.h にあり、次のように表示されます。  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  クラスまたはモジュールに同等の `Const` ステートメントを追加して、これらの定数をアプリケーションで使用できるようにします。  次に例を示します。  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### DLL プロシージャを呼び出すには  
  
1.  `Button1` という名前のボタンをプロジェクトのスタートアップ フォームに追加し、ボタンをダブルクリックしてコードを表示します。  ボタンのイベント ハンドラーが表示されます。  
  
2.  追加したボタンの `Click` イベント ハンドラーにプロシージャを呼び出すためのコードを追加し、適切な引数を指定します。  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  F5 キーを押してプロジェクトを実行します。  **\[はい\]** 応答ボタンと **\[いいえ\]** 応答ボタンのあるメッセージ ボックスが表示されます。  いずれかのボタンをクリックします。  
  
#### データのマーシャリング  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、Windows API 呼び出しで使用されるパラメーターと戻り値のデータ型が自動的に変換されますが、`MarshalAs` 属性を使用して、API が受け取るアンマネージ データ型を明示的に指定できます。  相互運用マーシャリングの詳細については、「[相互運用マーシャリング](../Topic/Interop%20Marshaling.md)」を参照してください。  
  
###### API 呼び出しで Declare および MarshalAs を使用するには  
  
1.  呼び出しの対象となる関数の名前、引数、データ型、および戻り値を確認します。  
  
2.  `MarshalAs` 属性へのアクセスを簡単にするために、クラスまたはモジュールのコードの先頭に `Imports` ステートメントを追加します。次に例を示します。  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  インポートした関数の関数プロトタイプを、使用するクラスまたはモジュールに追加します。また、パラメーターまたは戻り値に `MarshalAs` 属性を適用します。  次の例では、`void*` 型を受け取る API 呼び出しを `AsAny` としてマーシャリングしています。  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## DllImport による API 呼び出し  
 タイプ ライブラリを持たない DLL 内の関数を呼び出すもう 1 つの方法として、`DllImport` 属性があります。  `DllImport` は、`Declare` ステートメントを使用する場合とほぼ同じ働きをしますが、関数の呼び出し方をより細かく制御できます。  
  
 呼び出しが共有 \(*static* と呼ばれる場合もあります\) メソッドを参照している限り、ほとんどの Windows API 呼び出しで `DllImport` を使用できます。  クラスのインスタンスが必要なメソッドは使用できません。  `Declare` ステートメントとは異なり、`DllImport` では `MarshalAs` 属性を使用できません。  
  
#### DllImport 属性を使用して Windows API を呼び出すには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をクリックし、**\[プロジェクト\]** をクリックして、新規の Windows アプリケーション プロジェクトを開きます。  **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
2.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プロジェクト テンプレートの一覧の **\[Windows アプリケーション\]** を選択します。  新しいプロジェクトが表示されます。  
  
3.  `Button2` という名前のボタンをスタートアップ フォームに追加します。  
  
4.  `Button2` をダブルクリックしてフォームのコードを表示します。  
  
5.  `DllImport` へのアクセスを簡単にするために、スタートアップ フォーム クラスのコードの先頭に `Imports` ステートメントを追加します。  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  フォームの `End Class` ステートメントの前に空の関数を宣言し、`MoveFile` という名前を付けます。  
  
7.  関数宣言に `Public` 修飾子および `Shared` 修飾子を適用し、Windows API 関数で使用される引数に基づいて `MoveFile` のパラメーターを設定します。  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     関数は任意の有効なプロシージャ名を持つことができます。`DllImport` 属性によって、この名前が DLL で指定されます。  また、パラメーターと戻り値の相互運用性マーシャリングも処理されるため、API によって使用されるデータ型と同様の Visual Studio データ型を選択できます。  
  
8.  `DllImport` 属性を空の関数に適用します。  最初のパラメーターは、呼び出しの対象となる関数を含む DLL の名前と場所です。  Windows システム ディレクトリに格納されたファイルのパスを指定する必要はありません。  2 番目のパラメーターは、Windows API 内の関数の名前を指定する名前付き引数です。  この例では、`DllImport` 属性は `MoveFile` の呼び出しを強制的に KERNEL32.DLL 内の `MoveFileW` に転送します。  `MoveFileW` メソッドは、パス `src` からパス `dst` にファイルをコピーします。  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. 関数を呼び出すには、コードを `Button2_Click` イベント ハンドラーに追加します。  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Test.txt という名前のファイルを作成し、ハード ドライブ上の C:\\Tmp ディレクトリに配置します。  必要に応じて Tmp ディレクトリを作成します。  
  
11. F5 キーを押してアプリケーションを起動します。  メイン フォームが表示されます。  
  
12. **\[Button2\]** をクリックします。  ファイルを移動できる場合は、"The file was moved successfully" というメッセージが表示されます。  
  
## 参照  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [マネージ コードでのプロトタイプの作成](../Topic/Creating%20Prototypes%20in%20Managed%20Code.md)   
 [コールバック メソッドとしてのデリゲートのマーシャ リング](../Topic/Marshaling%20a%20Delegate%20as%20a%20Callback%20Method.md)
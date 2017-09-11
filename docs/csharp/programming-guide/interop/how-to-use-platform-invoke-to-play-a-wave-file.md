---
title: "方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 001236392d2b3d3c70dbd0faf2a899929dfe8625
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="c5dda-102">方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c5dda-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="c5dda-103">以下の C# コードの例では、プラットフォーム呼び出しサービスを使用して、Windows オペレーティング システム上の .wav サウンド ファイルを再生する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c5dda-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5dda-104">例</span><span class="sxs-lookup"><span data-stu-id="c5dda-104">Example</span></span>  
 <span data-ttu-id="c5dda-105">このコード例では、`DllImport` を使って `winmm.dll` の `PlaySound` メソッドのエントリ ポイントを `Form1 PlaySound()` としてインポートしています。</span><span class="sxs-lookup"><span data-stu-id="c5dda-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="c5dda-106">この例には、ボタンを含む簡単な Windows フォームがあります。</span><span class="sxs-lookup"><span data-stu-id="c5dda-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="c5dda-107">ボタンをクリックすると、Windows 標準の <xref:System.Windows.Forms.OpenFileDialog> ダイアログ ボックスが開き、再生するファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="c5dda-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="c5dda-108">Wave ファイルを選ぶと、winmm.DLL アセンブリ メソッドの `PlaySound()` メソッドを使って再生されます。</span><span class="sxs-lookup"><span data-stu-id="c5dda-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="c5dda-109">winmm.dll の `PlaySound` メソッドについて詳しくは、「[Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553)」(Waveform-Audio ファイルで PlaySound 関数を使用する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c5dda-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553).</span></span> <span data-ttu-id="c5dda-110">.wav 拡張子を持つファイルを参照して選び、**[開く]** をクリックすることで、プラットフォーム呼び出しを使って Wave ファイルを再生します。</span><span class="sxs-lookup"><span data-stu-id="c5dda-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="c5dda-111">テキスト ボックスに、選んだファイルの完全なパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5dda-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="c5dda-112">**[ファイルを開く]** ダイアログ ボックスは、次のフィルター設定によって拡張子 .wav を持つファイルのみを表示するようにフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="c5dda-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 <span data-ttu-id="c5dda-113">[!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c5dda-113">[!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]</span></span>  
  
 <span data-ttu-id="c5dda-114">[!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c5dda-114">[!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c5dda-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c5dda-115">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="c5dda-116">コードをコンパイルするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c5dda-116">To compile the code</span></span>  
  
1.  <span data-ttu-id="c5dda-117">Visual Studio で新しい C# Windows アプリケーション プロジェクトを作成し、**WinSound** という名前にします。</span><span class="sxs-lookup"><span data-stu-id="c5dda-117">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="c5dda-118">上記のコードをコピーし、`Form1.cs` ファイルに貼り付けて内容を上書きします。</span><span class="sxs-lookup"><span data-stu-id="c5dda-118">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="c5dda-119">次のコードをコピーし、`Form1.Designer.cs` ファイルのすべての既存コードの後の `InitializeComponent()` メソッドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c5dda-119">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     <span data-ttu-id="c5dda-120">[!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c5dda-120">[!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]</span></span>  
  
4.  <span data-ttu-id="c5dda-121">コードをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="c5dda-121">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c5dda-122">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c5dda-122">.NET Framework Security</span></span>  
 <span data-ttu-id="c5dda-123">詳細については、[.NET Framework セキュリティ](http://go.microsoft.com/fwlink/?LinkId=37122)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5dda-123">For more information, see [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dda-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5dda-124">See Also</span></span>  
 <span data-ttu-id="c5dda-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c5dda-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c5dda-126">[相互運用性の概要](../../../csharp/programming-guide/interop/interoperability-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c5dda-126">[Interoperability Overview](../../../csharp/programming-guide/interop/interoperability-overview.md) </span></span>  
 <span data-ttu-id="c5dda-127">[相互運用性の概要](../../../csharp/programming-guide/interop/interoperability-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c5dda-127">[Interoperability Overview](../../../csharp/programming-guide/interop/interoperability-overview.md) </span></span>  
 <span data-ttu-id="c5dda-128">[プラットフォーム呼び出しの詳細](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span><span class="sxs-lookup"><span data-stu-id="c5dda-128">[A Closer Look at Platform Invoke](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span></span>  
 [<span data-ttu-id="c5dda-129">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="c5dda-129">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)


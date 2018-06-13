---
title: ネイティブ相互運用性
description: .Net のネイティブ コンポーネントとやり取りする方法を説明します。
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 7da86cfe483a2355c53206f4c491fbd07e4c3046
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591925"
---
# <a name="native-interoperability"></a>ネイティブ相互運用性

このドキュメントでは、.NET で使用可能な "ネイティブ相互運用性" を実行する 3 つのすべての方法についてもう少し深く掘り下げます。

ネイティブ コードを呼び出す理由はいくつかあります。

*   オペレーティング システムには、マネージ クラス ライブラリに存在しない大量の API が付属しています。 この主な例には、ハードウェアまたはオペレーティング システム管理機能へのアクセスがあります。
*   C スタイル ABI (ネイティブ ABI) があるか、または生成できるその他のコンポーネントと通信します。 これはたとえば、[Java ネイティブ インターフェイス (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) によって公開されている Java コードまたはネイティブ コンポーネントを生成できる他のマネージ言語を対象とします。
*   Windows では、Microsoft Office スイートなどのインストールされるソフトウェアのほとんどが、それらのプログラムを表し、開発者が自動化したり、使用したりできる COM コンポーネントを登録します。 これも、ネイティブ相互運用性を必要とします。

もちろん、上の一覧は、開発者がネイティブ コンポーネントとやり取りしたいと考える、またはその必要があるすべての可能性のある状況やシナリオを取り上げていません。 たとえば、.NET クラス ライブラリは、ネイティブ相互運用性サポートを使用して、コンソールのサポートと操作、ファイル システムのアクセスなど、そのかなりの数の API を実装しています。 ただし、それを必要とする場合に、オプションがあることに注意することが重要です。

> [!NOTE]
> このドキュメントのほとんどの例は、.NET Core でサポートされる 3 つすべてのプラットフォーム (Windows、Linux、macOS) について提示しています。 ただし、短い解説的な例については、Windows ファイル名と拡張子 (つまり、ライブラリの場合は "dll") を使用する 1 つのサンプルだけを示します。 これは、それらの機能が Linux や macOS で使用できないわけではなく、単に便宜上のためにのみそうしています。

## <a name="platform-invoke-pinvoke"></a>プラットフォーム呼び出し (P/Invoke)

P/invoke は、アンマネージ ライブラリ内の構造体、コールバック、および関数をマネージ コードからアクセスできるようにするテクノロジです。 P/Invoke API のほとんどは、`System` と `System.Runtime.InteropServices` の 2 つの名前空間に含まれます。 これらの 2 つの名前空間を使用して、ネイティブ コンポーネントと通信する方法を記述する属性にアクセスできます。

最も一般的な例から始めましょう。これはマネージ コードでアンマネージ関数を呼び出します。 コマンドライン アプリケーションからメッセージ ボックスを表示してみましょう。

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

上の例はとても簡単ですが、マネージ コードからアンマネージ関数を呼び出すために必要なことを示しています。 この例の手順を説明します。

*   1 行目は、必要なすべての項目を保持する名前空間 `System.Runtime.InteropServices` のステートメントの使用を示しています。
*   5 行目で `DllImport` 属性を導入しています。 この属性は、ランタイムにアンマネージ DLL を読み込むように伝えるため、きわめて重要です。 これは、呼び出したい DLL です。
*   6 行目は、P/Invoke 作業の最も重要な箇所です。 ここでは、アンマネージと**正確に同じシグネチャ**を持つマネージ メソッドを定義しています。 宣言には新しいキーワード `extern` があることがわかります。これはランタイムに、これが外部メソッドであり、それを呼び出したときに、ランタイムが `DllImport` 属性に指定された DLL からそれを見つける必要があることを伝えます。

例の残りの部分は、その他のマネージ メソッドと同じように、メソッドを呼び出しているだけです。

サンプルは、macOS の場合も似ています。 変更する必要がある唯一の点が、当然ながら、`DllImport` 属性内のライブラリの名前です。macOS のダイナミック ライブラリの名前付けのスキームが異なるからです。 下のサンプルでは、`getpid(2)` 関数を使用して、アプリケーションのプロセス ID を取得し、それをコンソールに出力しています。

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libSystem shared library and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

これは Linux でも同様です。 `getpid(2)` は標準的な [POSIX](https://en.wikipedia.org/wiki/POSIX) システム コールであるため、関数名が同じです。

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc shared library and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

### <a name="invoking-managed-code-from-unmanaged-code"></a>アンマネージ コードからのマネージ コードの呼び出し

もちろん、ランタイムは、通信が双方向にフローすることを許可しているため、関数ポインターを使用して、ネイティブ関数からマネージ成果物を呼び出すことができます。 マネージ コードで、関数ポインターに最も近いものが、**デリゲート**であるため、これをネイティブ コードからマネージ コードへのコールバックを許可するために使います。

この機能を使用する方法は、先述のマネージからネイティブへのプロセスに似ています。 指定されたコールバックに対し、ユーザーがシグネチャと一致するデリゲートを定義し、それを外部メソッドに渡します。 ランタイムは、他のすべてのことを処理します。

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

例の手順に従う前に、使用する必要があるアンマネージ関数のシグネチャについて見直しておくのはよいことです。 すべてのウィンドウを列挙するために呼び出す関数は、次のシグネチャを持ちます。`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

最初のパラメーターでは、コールバックです。 上記のコールバックのシグネチャは次のとおりです。`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

これを踏まえて、例の手順を追っていきましょう。

*   例の 8 行目では、アンマネージ コードからのコールバックのシグネチャと一致するデリゲートを定義しています。 マネージ コードで `IntPtr` を使用して、LPARAM および HWND 型を表す方法に注意してください。
*   10 行目と 11 行目では、user32.dll ライブラリから `EnumWindows` 関数を導入しています。
*   13 ～ 16 行目は、デリゲートを実装しています。 この簡単な例では、ハンドルだけコンソールに出力します。
*   最後に、19 行目で、外部メソッドを呼び出し、デリゲートを渡しています。

Linux と macOS の例を、以下に示します。 それらの場合、`libc` C ライブラリに見つかる `ftw` 関数を使用します。 この関数は、ディレクトリ階層をスキャンするために使用し、そのパラメーターの 1 つとして、関数へのポインターを受け取ります。 上記のメソッドのシグネチャは次のとおりです。`int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

macOS の例では、同じ関数を使用していますが、唯一の違いは `DllImport` 属性への引数です。macOS は `libc` を別の場所で保持しているためです。

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code. You can find more information
        // about this in the section on marshalling below.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

上記の例のどちらも、パラメーターに依存し、どちらの場合もパラメーターは、マネージ型として指定されています。 ランタイムは、"正しいこと" を実行し、これらを他方の側で同等のものに処理します。 このプロセスでは、高品質なネイティブ相互運用コードを記述することがきわめて重要であるため、ランタイムが型を_マーシャリング_する際に何が起こるかを見てみましょう。

## <a name="type-marshalling"></a>型のマーシャリング

**マーシャ リング**はマネージの境界を越えてネイティブに、またはその逆の必要がある場合に、型を変換するプロセスです。

マーシャリングが必要な理由は、マネージ コードとアンマネージ コード内の型が異なるためです。 マネージ コードで、たとえば、`String` があるとします。アンマネージ環境では、文字列は Unicode ("ワイド")、Unicode 以外、Null 終了、ASCII などです。既定で、P/Invoke サブシステムは既定の動作に基づいて "正しいこと" をしようと試みますが、それらについては [MSDN](../../docs/framework/interop/default-marshaling-behavior.md) で確認できます。 ただし、特別な制御が必要な場合、`MarshalAs` 属性を採用して、アンマネージ側で期待する型を指定します。 たとえば、文字列を NULL で終わる ANSI 文字列として送信させる場合は、次のように指定できます。

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a>クラスと構造体のマーシャリング

型のマーシャリングの別の側面は、構造体をアンマネージ メソッドに渡す方法です。 たとえば、一部のアンマネージ メソッドでは、パラメーターとして構造体が必要です。 このような場合、環境のマネージ部分に対応する構造体またはクラスを作成し、それをパラメーターとして使用する必要があります。 ただし、クラスを定義するだけでは不十分で、マーシャラーに、クラス内のフィールドをアンマネージ構造体にマップする方法を指示する必要もあります。 これは、`StructLayout` 属性が関与する箇所です。

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

上の例は、`GetSystemTime()` 関数を呼び出す簡単な例を示しています。 興味深いビットは 4 行目にあります。 この属性は、他方 (アンマネージ) の側でクラスのフィールドを構造体に順番にマップする必要があることを指定します。 このことは、下に示すアンマネージ構造体に対応する必要があるため、フィールドの名前付けは重要でなく、それらの順番だけが重要であることを意味します。

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

前の例で、これの Linux と macOS の例について既に説明しました。 下にもう一度示します。

```csharp
[StructLayout(LayoutKind.Sequential)]
public class StatClass {
        public uint DeviceID;
        public uint InodeNumber;
        public uint Mode;
        public uint HardLinks;
        public uint UserID;
        public uint GroupID;
        public uint SpecialDeviceID;
        public ulong Size;
        public ulong BlockSize;
        public uint Blocks;
        public long TimeLastAccess;
        public long TimeLastModification;
        public long TimeLastStatusChange;
}
```

`StatClass` クラスは、UNIX システムで `stat` システム コールによって返される構造体を表します。 これは、指定したファイルに関する情報を表します。 上のクラスは、マネージ コードでの stat 構造体表現です。 ここでも、クラス内のフィールドはネイティブ構造体と同じ順番である必要があり (これらについては、任意の UNIX 実装の man ページを調べて参照できます)、基になる型が同じである必要があります。

## <a name="more-resources"></a>その他のリソース

*   [PInvoke.net wiki](https://www.pinvoke.net/) は、一般的な Win32 API とそれらを呼び出す方法に関する情報を記載した優れた Wiki です。
*   [MSDN の P/Invoke](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [P/invoke に関する Mono のドキュメント](https://www.mono-project.com/docs/advanced/pinvoke/)

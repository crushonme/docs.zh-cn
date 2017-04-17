---
title: "64 位应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "64 位应用程序 [C++]"
  - "64 位编程 [C++]"
  - "应用程序 [C++], 64 位"
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
caps.latest.revision: 53
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 53
---
# 64 位应用程序
编译应用程序时，您可以将其指定为在 Windows 64 位操作系统上作为本机应用程序或在 WOW64（Windows 64 位下的 Windows 32 位）下运行。  WOW64 是一种兼容性环境，它使 32 位应用能够在 64 位系统上运行。  WOW64 包括在所有 64 位版本的 Windows 操作系统中。  
  
## 在 Windows 上运行 32 位与64 位应用程序  
 在 64 位操作系统上，所有基于 .NET Framework 1.0 或 1.1 生成的应用程序都会被视为 32 位应用程序，并始终在 WOW64 和 32 位公共语言运行时 \(CLR\) 下执行。  基于 [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] 或更晚版本生成的 32 位应用程序在 64 位系统上也会的 WOW64 下运行。  
  
 在 x86 计算机上，Visual Studio 会安装 32 位版本的 CLR，而在 64 位 Windows 计算机上会同时安装 32 位版本和适当的 64 位版本的 CLR。  （因为 Visual Studio 是一个 32 位应用程序，所以当安装到 64 位系统上时，它会在 WOW64 下运行。）  
  
> [!NOTE]
>  由于 Itanium 处理器系列的 x86 仿真和 WOW64 子系统设计，仅限在一个处理器上执行应用程序。  这些因素会降低在基于 Itanium 的系统上运行的 32 位 .NET Framework 应用程序的性能和可伸缩性。  我们建议您使用 [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)]，它包括对基于 Itanium 系统的本机 64 位支持，以提升性能和可伸缩性。  
  
 默认情况下，在 64 位 Windows 操作系统上运行 64 位托管应用程序时，您可以创建一个不超过 2 GB 的对象。  然而，在 [!INCLUDE[net_v45](../../includes/net-v45-md.md)] 中，您可以增加该限制。  有关详细信息，请参阅 [\<gcAllowVeryLargeObjects\> 元素](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)。  
  
 很多程序集可在 32 位 CLR 和 64 位 CLR 上同样运行。  然而，因为包含下列一个或多个原因，对于不同的 CLR，有些程序可能会有不同表现：  
  
-   结构中包含大小随平台而改变的成员，例如任何指针类型。  
  
-   指针算术包含固定大小。  
  
-   平台调用错误，或使用句柄的 `Int32` 而非 `IntPtr` 的 COM 声明不正确。  
  
-   将 `IntPtr` 转换到 `Int32` 的代码。  
  
 有关如何移植 32 位应用程序以使其在 64 位 CLR 上运行的详细信息，请参阅 MSDN 库中的[将 32 位托管代码迁移至 64 位](http://go.microsoft.com/fwlink/?LinkId=150542)。  
  
## 常规 64 位编程信息  
 有关 64 位编程的常规信息，请参阅以下文档：  
  
-   有关 64 位 Windows 计算机上的 64 位版 CLR 的详细信息，请参阅 MSDN 网站上的 [.NET Framework 开发人员中心](http://go.microsoft.com/fwlink/?LinkId=37079)。  
  
-   请参阅 [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] 文档中的 [64 位 Windows 编程指南](http://go.microsoft.com/fwlink/p/?LinkId=253512)。  
  
-   有关如何下载 64 位版本 CLR 的信息，请参阅 MSDN 网站上的 [.NET Framework 开发人员中心下载](http://go.microsoft.com/fwlink/?LinkId=50953)。  
  
-   有关用于创建 64 位应用程序的 Visual Studio 支持的信息，请参阅 [Visual Studio IDE 64 位支持](../Topic/Visual%20Studio%20IDE%2064-Bit%20Support.md)。  
  
## 创建 64 位应用程序的编译器支持  
 默认情况下，如果您使用 .NET Framework 在 32 位或 64 位计算机中生成一个应用程序，该应用程序将会在 64 位计算机中作为本机应用程序运行（即不是在 WOW64 下运行）。  有关如何使用 Visual Studio 编译器创建 64 位应用程序，并且应用程序会作为本机应用程序运行和\/或在 WOW64 下运行的信息，请参阅下表中的文档。  
  
|编译器|编译器选项|  
|---------|-----------|  
|Visual Basic|[\/platform](../Topic/-platform%20\(Visual%20Basic\).md)|  
|Visual C\#|[\/platform \(Specify Output Platform\)](../Topic/-platform%20\(C%23%20Compiler%20Options\).md)|  
|Visual C\+\+|可以通过使用 **\/clr:safe** 创建与平台无关的 Microsoft 中间语言 \(MSIL\) 应用程序。  有关详细信息，请参阅 [\/clr（公共语言运行时编译）](../Topic/-clr%20\(Common%20Language%20Runtime%20Compilation\).md)。<br /><br /> Visual c\+\+ 为每个 64 位操作系统均包括一个单独的编译器。  有关如何使用 Visual C\+\+ 创建在 64 位 Windows 操作系统上运行的本机应用程序的详细信息，请参阅 [64 位编程](http://msdn.microsoft.com/library/h2k70f3s\(v=vs.80\))。|  
  
## 确定 .exe 文件或 .dll 文件的状态  
 若要确定 .exe 文件或 .dll 文件只能在某个特定平台中运行还是可在 WOW64 下运行，只能使用 [CorFlags.exe（CorFlags 转换工具）](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md)。  您也可以使用 CorFlags.exe 更改 .exe 文件或 .dll 文件的平台状态。  Visual Studio 程序集的 CLR 头的主运行时版本号设置为 2，次运行时版本号设置为 5。  将次运行时版本设置为 0 的应用程序会被视为旧版应用程序，且始终在 WOW64 下执行。  
  
 若要以编程方式查询 .exe 或 .dll，以查看其是只能在特定平台上运行还是在 WOW64 下运行，请使用 <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=fullName> 方法。
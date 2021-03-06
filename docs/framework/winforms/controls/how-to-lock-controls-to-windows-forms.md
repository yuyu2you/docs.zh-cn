---
title: 如何：将控件锁定到 Windows 窗体
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d157ddc8be4b5fa0057241b562e76b566e8dad99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458340"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>如何：将控件锁定到 Windows 窗体

设计 Windows 应用程序的用户界面（UI）时，可以在控件定位正确之后锁定控件，以便在设置其他属性时不会无意中移动或调整它们的大小。

此外，您还可以同时锁定和解锁窗体上的所有控件，这对于具有许多控件的窗体非常有用，或者您可以对各个控件解除锁定。 将所有控件置于窗体上所需的位置后，请将它们全部锁定，以防错误移动。

## <a name="to-lock-a-control"></a>锁定控件

在 Visual Studio 的 "**属性**" 窗口中，选择 "**锁定**" 属性，然后选择 " **true**"。 （双击该名称将切换属性设置。）

或者，右键单击控件，然后选择 "**锁定控件**"。

> [!NOTE]
> 锁定控件可防止将其拖动到设计图面上的新大小或位置。 但是，您仍然可以通过 "**属性**" 窗口或代码来更改控件的大小或位置。

## <a name="to-lock-all-the-controls-on-a-form"></a>锁定窗体上的所有控件

从 "**格式**" 菜单中选择 "**锁定控件**"。

> [!NOTE]
> 此命令也会锁定窗体的大小，因为窗体是一个控件。

## <a name="to-unlock-all-locked-controls-on-a-form"></a>解锁窗体上的所有锁定控件

从 "**格式**" 菜单中选择 "**锁定控件**"。

窗体上所有以前锁定的控件现在都未被锁定。

## <a name="to-unlock-locked-controls-individually"></a>单独解锁锁定的控件

在 "**属性**" 窗口中，选择 "**锁定**" 属性，然后选择 " **false**"。 （双击该名称将切换属性设置。）

## <a name="see-also"></a>请参阅

- [Windows 窗体控件](index.md)
- [标记各个 Windows 窗体控件并创建它们的快捷键](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
- [按功能列出的 Windows 窗体控件](windows-forms-controls-by-function.md)

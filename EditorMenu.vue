<template>
  <div>
    <div class="relative text-black inline-flex h-full leading-none gap-0.5 flex-row p-1 items-center bg-white dark:bg-black border-neutral-200 dark:border-neutral-800">
      <button class="group btnBase" type="button" id="radix-:r3:" aria-haspopup="menu" aria-expanded="false" data-state="closed" @click="toggleHierarchyDropdown" ref="hierarchyButton">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-pilcrow w-4 h-4">
          <path d="M13 4v16"></path>
          <path d="M17 4v16"></path>
          <path d="M19 4H9.5a4.5 4.5 0 0 0 0 9H13"></path></svg
        ><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-chevron-down w-2 h-2"><path d="m6 9 6 6 6-6"></path></svg>
      </button>
      <div v-if="isHierarchyDropdownOpen" data-radix-popper-content-wrapper="" dir="ltr" :style="{ position: 'absolute', left: 0, top: '3rem', minWidth: 'max-content', '--radix-popper-transform-origin': '50% 0px', zIndex: '40' }">
        <div class="flex flex-col gap-1 px-2 py-4 bg-white rounded-lg dark:bg-black shadow-sm border border-neutral-200 dark:border-neutral-800" data-side="bottom" data-align="center" role="menu" aria-orientation="vertical" data-state="open" data-radix-menu-content="" dir="ltr" id="radix-:r4:" aria-labelledby="radix-:r3:" tabindex="-1" data-orientation="vertical" style="outline: none">
          <div class="mt-2 first:mt-0"><div class="text-[.65rem] font-semibold mb-1 uppercase text-neutral-500 dark:text-neutral-400 px-1.5">Hierarchy</div></div>
          <button @click="setParagraph" :class="['dropdownBtn', getClass('paragraph')]">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-pilcrow w-4 h-4 mr-1">
              <path d="M13 4v16"></path>
              <path d="M17 4v16"></path>
              <path d="M19 4H9.5a4.5 4.5 0 0 0 0 9H13"></path>
            </svg>
            Paragraph
          </button>
          <button @click="setHeading(1)" :class="['dropdownBtn', getClass('heading', { level: 1 })]">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-heading1 w-4 h-4 mr-1">
              <path d="M4 12h8"></path>
              <path d="M4 18V6"></path>
              <path d="M12 18V6"></path>
              <path d="m17 12 3-2v8"></path>
            </svg>
            Heading 1
          </button>
          <button @click="setHeading(2)" :class="['dropdownBtn', getClass('heading', { level: 2 })]">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-heading2 w-4 h-4 mr-1">
              <path d="M4 12h8"></path>
              <path d="M4 18V6"></path>
              <path d="M12 18V6"></path>
              <path d="M21 18h-4c0-4 4-3 4-6 0-1.5-2-2.5-4-1"></path>
            </svg>
            Heading 2
          </button>
          <button @click="setHeading(3)" :class="['dropdownBtn', getClass('heading', { level: 3 })]">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-heading3 w-4 h-4 mr-1">
              <path d="M4 12h8"></path>
              <path d="M4 18V6"></path>
              <path d="M12 18V6"></path>
              <path d="M17.5 10.5c1.7-1 3.5 0 3.5 1.5a2 2 0 0 1-2 2"></path>
              <path d="M17 17.5c2 1.5 4 .3 4-1.5a2 2 0 0 0-2-2"></path>
            </svg>
            Heading 3
          </button>
          <div class="mt-2 first:mt-0"><div class="text-[.65rem] font-semibold mb-1 uppercase text-neutral-500 dark:text-neutral-400 px-1.5">Lists</div></div>
          <button @click="toggleBulletList" :class="['dropdownBtn', getClass('bulletList')]">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-list w-4 h-4 mr-1">
              <path d="M3 12h.01"></path>
              <path d="M3 18h.01"></path>
              <path d="M3 6h.01"></path>
              <path d="M8 12h13"></path>
              <path d="M8 18h13"></path>
              <path d="M8 6h13"></path>
            </svg>
            Bullet list
          </button>
          <button @click="toggleOrderedList" :class="['dropdownBtn', getClass('orderedList')]">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-list-ordered w-4 h-4 mr-1">
              <path d="M10 12h11"></path>
              <path d="M10 18h11"></path>
              <path d="M10 6h11"></path>
              <path d="M4 10h2"></path>
              <path d="M4 6h1v4"></path>
              <path d="M6 18H4c0-1 2-2 2-3s-1-1.5-2-1"></path>
            </svg>
            Numbered list
          </button>
        </div>
      </div>
      <button class="group btnBase" type="button" id="radix-:r5:" aria-haspopup="menu" aria-expanded="false" data-state="closed" @click="setFontFamily('Inter')">
        <span style="vertical-align: inherit">{{ editor.getAttributes('textStyle').fontFamily??'Ninguno' }}</span>
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-chevron-down w-2 h-2"><path d="m6 9 6 6 6-6"></path></svg>
      </button>
      <div data-radix-popper-content-wrapper="" dir="ltr" style="position: absolute; left: 0px; top: 3rem; min-width: max-content; --radix-popper-transform-origin: 50% 0px; z-index: 40; --radix-popper-available-width: 1064.0005683634179px; --radix-popper-available-height: 516px; --radix-popper-anchor-width: 61.09378263482383px; --radix-popper-anchor-height: 32px">
        <div class="flex flex-col gap-1 px-2 py-4 bg-white rounded-lg dark:bg-black shadow-sm border border-neutral-200 dark:border-neutral-800" data-side="bottom" data-align="center" role="menu" aria-orientation="vertical" data-state="open" data-radix-menu-content="" dir="ltr" id="radix-:r6:" aria-labelledby="radix-:r5:" tabindex="-1" data-orientation="vertical" style="outline: none; --radix-dropdown-menu-content-transform-origin: var(--radix-popper-transform-origin); --radix-dropdown-menu-content-available-width: var(--radix-popper-available-width); --radix-dropdown-menu-content-available-height: var(--radix-popper-available-height); --radix-dropdown-menu-trigger-width: var(--radix-popper-anchor-width); --radix-dropdown-menu-trigger-height: var(--radix-popper-anchor-height); pointer-events: auto">
          <div class="mt-2.5 first:mt-0 gap-0.5 flex flex-col">
            <div class="text-[.65rem] font-semibold mb-1 uppercase text-neutral-500 dark:text-neutral-400 px-1.5">Sans Serif</div>
            <button @click="editor.chain().focus().setFontFamily('Inter').run()" :class="['dropdownBtn', getClass('textStyle', { fontFamily: 'Inter' })]"><span>Inter</span></button>
            <button @click="editor.chain().focus().setFontFamily('Arial').run()" :class="['dropdownBtn', getClass('textStyle', { fontFamily: 'Arial' })]"><span style="font-family: Arial">Arial</span></button>
            <button @click="editor.chain().focus().setFontFamily('Helvetica').run()" :class="['dropdownBtn', getClass('textStyle', { fontFamily: 'Arial' })]"><span style="font-family: Helvetica">Helvetica</span></button>
          </div>
          <div class="mt-2.5 first:mt-0 gap-0.5 flex flex-col">
            <div class="text-[.65rem] font-semibold mb-1 uppercase text-neutral-500 dark:text-neutral-400 px-1.5">Serif</div>
            <button @click="editor.chain().focus().setFontFamily('Times New Roman').run()" :class="['dropdownBtn', getClass('textStyle', { fontFamily: 'Times New Roman' })]"><span style="font-family: Times">Times New Roman</span></button>
            <button @click="editor.chain().focus().setFontFamily('Garamond').run()" :class="['dropdownBtn', getClass('textStyle', { fontFamily: 'Garamond' })]"><span style="font-family: Garamond">Garamond</span></button>
            <button @click="editor.chain().focus().setFontFamily('Georgia').run()" :class="['dropdownBtn', getClass('textStyle', { fontFamily: 'Georgia' })]"><span style="font-family: Georgia">Georgia</span></button>
          </div>
          <div class="mt-2.5 first:mt-0 gap-0.5 flex flex-col">
            <div class="text-[.65rem] font-semibold mb-1 uppercase text-neutral-500 dark:text-neutral-400 px-1.5">Monospace</div>
            <button @click="editor.chain().focus().setFontFamily('Courier').run()" :class="['dropdownBtn', getClass('textStyle', { fontFamily: 'Courier' })]"><span style="font-family: Courier">Courier</span></button>
            <button @click="editor.chain().focus().setFontFamily('Courier New').run()" :class="['dropdownBtn', getClass('textStyle', { fontFamily: 'Courier New' })]"><span style="font-family: 'Courier New'">Courier New</span></button>
          </div>
        </div>
      </div>
      <button class="group btnBase" type="button" id="radix-:r7:" aria-haspopup="menu" aria-expanded="false" data-state="closed" @click="setFontWeight('medium')">
        <span style="vertical-align: inherit">Medium</span>
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-chevron-down w-2 h-2"><path d="m6 9 6 6 6-6"></path></svg>
      </button>
      <div class="bg-neutral-200 dark:bg-neutral-800 h-full min-h-[1.5rem] w-[1px] mx-1 first:ml-0 last:mr-0"></div>
      <span>
        <button @click="editor.chain().focus().toggleBold().run()" :class="getClass('bold')" class="group btnBase">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-bold w-4 h-4">
            <path d="M6 12h9a4 4 0 0 1 0 8H7a1 1 0 0 1-1-1V5a1 1 0 0 1 1-1h7a4 4 0 0 1 0 8"></path>
          </svg>
        </button>
      </span>
      <span>
        <button @click="editor.chain().focus().toggleItalic().run()" :class="getClass('italic')" class="group btnBase">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-italic w-4 h-4">
            <line x1="19" x2="10" y1="4" y2="4"></line>
            <line x1="14" x2="5" y1="20" y2="20"></line>
            <line x1="15" x2="9" y1="4" y2="20"></line>
          </svg>
        </button>
      </span>
      <span>
        <button @click="editor.chain().focus().toggleUnderline().run()" :class="getClass('underline')" class="group btnBase">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-underline w-4 h-4">
            <path d="M6 4v6a6 6 0 0 0 12 0V4"></path>
            <line x1="4" x2="20" y1="20" y2="20"></line>
          </svg>
        </button>
      </span>
      <span>
        <button @click="editor.chain().focus().toggleStrike().run()" :class="getClass('strike')" class="group btnBase">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-strikethrough w-4 h-4">
            <path d="M16 4H9a3 3 0 0 0-2.83 4"></path>
            <path d="M14 12a4 4 0 0 1 0 8H6"></path>
            <line x1="4" x2="20" y1="12" y2="12"></line>
          </svg>
        </button>
      </span>
      <span>
        <button @click="editor.chain().focus().toggleCodeBlock().run()" :class="getClass('codeBlock')" class="group btnBase">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-code w-4 h-4">
            <polyline points="16 18 22 12 16 6"></polyline>
            <polyline points="8 6 2 12 8 18"></polyline>
          </svg>
        </button>
      </span>
      <span>
        <button @click="editor.chain().focus().toggleCodeBlock().run()" class="group btnBase">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-file-code w-4 h-4">
            <path d="M10 12.5 8 15l2 2.5"></path>
            <path d="m14 12.5 2 2.5-2 2.5"></path>
            <path d="M14 2v4a2 2 0 0 0 2 2h4"></path>
            <path d="M15 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V7z"></path>
          </svg>
        </button>
      </span>
      <span>
        <button @click="insertLink()" class="group btnBase" type="button" aria-haspopup="dialog" aria-expanded="false" aria-controls="radix-:r9:" data-state="closed">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-link w-4 h-4">
            <path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path>
            <path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path>
          </svg>
        </button>
      </span>
      <span>
        <button @click="toggleHighlight()" :class="getClass('highlight')" class="group btnBase" type="button" aria-haspopup="dialog" aria-expanded="false" aria-controls="radix-:ra:" data-state="closed">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-highlighter w-4 h-4">
            <path d="m9 11-6 6v3h9l3-3"></path>
            <path d="m22 12-4.6 4.6a2 2 0 0 1-2.8 0l-5.2-5.2a2 2 0 0 1 0-2.8L14 4"></path>
          </svg>
        </button>
      </span>
      <span>
        <button @click="toggleColorPalette" class="group btnBase" type="button" aria-haspopup="dialog" aria-expanded="false" aria-controls="radix-:rb:" data-state="closed">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-palette w-4 h-4">
            <circle cx="13.5" cy="6.5" r=".5" fill="currentColor"></circle>
            <circle cx="17.5" cy="10.5" r=".5" fill="currentColor"></circle>
            <circle cx="8.5" cy="7.5" r=".5" fill="currentColor"></circle>
            <circle cx="6.5" cy="12.5" r=".5" fill="currentColor"></circle>
            <path d="M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10c.926 0 1.648-.746 1.648-1.688 0-.437-.18-.835-.437-1.125-.29-.289-.438-.652-.438-1.125a1.64 1.64 0 0 1 1.668-1.668h1.996c3.051 0 5.555-2.503 5.555-5.554C21.965 6.012 17.461 2 12 2z"></path>
          </svg>
        </button>
      </span>
      <div v-if="isColorPaletteOpen" data-radix-popper-content-wrapper="" style="position: absolute; right: 0px; top: 3rem; min-width: max-content; --radix-popper-transform-origin: 50% 0px; z-index: 40; --radix-popper-available-width: 836.0004465712568px; --radix-popper-available-height: 422px; --radix-popper-anchor-width: 34.00001816198891px; --radix-popper-anchor-height: 32px">
        <div class="bg-white rounded-lg dark:bg-black shadow-sm border border-neutral-200 dark:border-neutral-800" data-side="bottom" data-align="center" data-state="open" role="dialog" id="radix-:rb:" tabindex="-1" style="--radix-popover-content-transform-origin: var(--radix-popper-transform-origin); --radix-popover-content-available-width: var(--radix-popper-available-width); --radix-popover-content-available-height: var(--radix-popper-available-height); --radix-popover-trigger-width: var(--radix-popper-anchor-width); --radix-popover-trigger-height: var(--radix-popper-anchor-height)">
          <input @input="editor.chain().focus().setColor($event.target.value).run()" type="color" :value="editor.getAttributes('textStyle').color" class="w-full h-[50px] p-2 text-black bg-white border rounded dark:bg-black dark:text-white border-neutral-200 dark:border-neutral-800 focus:outline-1 focus:ring-0 focus:outline-neutral-300 dark:focus:outline-neutral-700" />
          <div class="flex flex-wrap items-center gap-1 max-w-[15rem]">
            <button @click="editor.chain().focus().setColor('#fb7185').run()" :class="{ 'is-active': editor.isActive('textStyle', { color: '#fb7185' }) }" class="flex items-center justify-center px-1.5 py-1.5 rounded group hover:bg-neutral-100"><div class="w-4 h-4 rounded bg-slate-100 shadow-sm ring-offset-2 ring-current hover:ring-1" style="background-color: #fb7185; color: #fb7185"></div></button>
            <button class="flex items-center justify-center px-1.5 py-1.5 rounded group hover:bg-neutral-100"><div class="w-4 h-4 rounded bg-slate-100 shadow-sm ring-offset-2 ring-current hover:ring-1" style="background-color: rgb(253, 186, 116); color: rgb(253, 186, 116)"></div></button>
            <button class="flex items-center justify-center px-1.5 py-1.5 rounded group hover:bg-neutral-100"><div class="w-4 h-4 rounded bg-slate-100 shadow-sm ring-offset-2 ring-current hover:ring-1" style="background-color: rgb(217, 249, 157); color: rgb(217, 249, 157)"></div></button>
            <button class="flex items-center justify-center px-1.5 py-1.5 rounded group hover:bg-neutral-100"><div class="w-4 h-4 rounded bg-slate-100 shadow-sm ring-offset-2 ring-current hover:ring-1" style="background-color: rgb(167, 243, 208); color: rgb(167, 243, 208)"></div></button>
            <button class="flex items-center justify-center px-1.5 py-1.5 rounded group hover:bg-neutral-100"><div class="w-4 h-4 rounded bg-slate-100 shadow-sm ring-offset-2 ring-current hover:ring-1" style="background-color: rgb(165, 243, 252); color: rgb(165, 243, 252)"></div></button>
            <button class="flex items-center justify-center px-1.5 py-1.5 rounded group hover:bg-neutral-100"><div class="w-4 h-4 rounded bg-slate-100 shadow-sm ring-offset-2 ring-current hover:ring-1" style="background-color: rgb(165, 180, 252); color: rgb(165, 180, 252)"></div></button>
            <span>
              <button class="group btnBase">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-undo w-4 h-4">
                  <path d="M3 7v6h6"></path>
                  <path d="M21 17a9 9 0 0 0-9-9 9 9 0 0 0-6 2.3L3 13"></path>
                </svg>
              </button>
            </span>
          </div>
        </div>
      </div>
      <span>
        <button @click="toggleEllipsisDropdown" class="group btnBase" type="button" aria-haspopup="dialog" aria-expanded="false" aria-controls="radix-:rc:" data-state="closed" ref="ellipsisButton">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-ellipsis-vertical w-4 h-4">
            <circle cx="12" cy="12" r="1"></circle>
            <circle cx="12" cy="5" r="1"></circle>
            <circle cx="12" cy="19" r="1"></circle>
          </svg>
        </button>
        <div v-if="isEllipsisDropdownOpen" data-radix-popper-content-wrapper="" :style="{ position: 'absolute', right: 0, top: '3rem', minWidth: 'max-content', '--radix-popper-transform-origin': '50% 42px', 'z-index': '40' }">
          <div class="text-black inline-flex h-full leading-none gap-0.5 flex-row p-1 items-center bg-white rounded-lg dark:bg-black shadow-sm border border-neutral-200 dark:border-neutral-800" data-side="top" data-align="center" data-state="open" role="dialog" id="radix-:rc:" tabindex="-1" style="">
            <span>
              <button @click="editor.chain().focus().toggleSubscript().run()" :class="{ 'is-active': editor.isActive('subscript') }" class="group btnBase">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-subscript w-4 h-4">
                  <path d="m4 5 8 8"></path>
                  <path d="m12 5-8 8"></path>
                  <path d="M20 19h-4c0-1.5.44-2 1.5-2.5S20 15.33 20 14c0-.47-.17-.93-.48-1.29a2.11 2.11 0 0 0-2.62-.44c-.42.24-.74.62-.9 1.07"></path>
                </svg>
              </button>
            </span>
            <span>
              <button @click="editor.chain().focus().toggleSuperscript().run()" :class="{ 'is-active': editor.isActive('superscript') }" class="group btnBase">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-superscript w-4 h-4">
                  <path d="m4 19 8-8"></path>
                  <path d="m12 19-8-8"></path>
                  <path d="M20 12h-4c0-1.5.442-2 1.5-2.5S20 8.334 20 7.002c0-.472-.17-.93-.484-1.29a2.105 2.105 0 0 0-2.617-.436c-.42.239-.738.614-.899 1.06"></path>
                </svg>
              </button>
            </span>
            <div class="bg-neutral-200 dark:bg-neutral-800 h-full min-h-[1.5rem] w-[1px] mx-1 first:ml-0 last:mr-0"></div>
            <span>
              <button @click="editor.chain().focus().setTextAlign('left').run()" :class="{ 'is-active': editor.isActive({ textAlign: 'left' }) }" class="group btnBase">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-align-left w-4 h-4">
                  <path d="M15 12H3"></path>
                  <path d="M17 18H3"></path>
                  <path d="M21 6H3"></path>
                </svg>
              </button>
            </span>
            <span>
              <button @click="editor.chain().focus().setTextAlign('center').run()" :class="{ 'is-active': editor.isActive({ textAlign: 'center' }) }" class="group btnBase">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-align-center w-4 h-4">
                  <path d="M17 12H7"></path>
                  <path d="M19 18H5"></path>
                  <path d="M21 6H3"></path>
                </svg>
              </button>
            </span>
            <span>
              <button @click="editor.chain().focus().setTextAlign('right').run()" :class="{ 'is-active': editor.isActive({ textAlign: 'right' }) }" class="group btnBase">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-align-right w-4 h-4">
                  <path d="M21 12H9"></path>
                  <path d="M21 18H7"></path>
                  <path d="M21 6H3"></path>
                </svg>
              </button>
            </span>
            <span>
              <button @click="editor.chain().focus().setTextAlign('justify').run()" :class="{ 'is-active': editor.isActive({ textAlign: 'justify' }) }" class="group btnBase">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-align-justify w-4 h-4">
                  <path d="M3 12h18"></path>
                  <path d="M3 18h18"></path>
                  <path d="M3 6h18"></path>
                </svg>
                Justify
              </button>
            </span>
          </div>
        </div>
      </span>
    </div>

    <floating-menu :editor="editor" :tippy-options="{ duration: 100 }" v-if="editor">
      <button class="float-btn" @click="insertHorizontalRule()">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" aria-hidden="true" role="img" class="iconify iconify--mdi" width="32" height="32" preserveAspectRatio="xMidYMid meet" viewBox="0 0 24 24">
          <path fill="currentColor" d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2Z"></path>
        </svg>
      </button>
    </floating-menu>
  </div>
</template>

<script setup>
import { ref, reactive, computed } from "vue";
import { FloatingMenu } from "@tiptap/vue-3";

defineOptions({
  styleIsolation: "scoped",
});
const props = defineProps({
  editor: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["editor-updated"]);

const isEllipsisDropdownOpen = ref(false);
const isHierarchyDropdownOpen = ref(false);
const ellipsisButton = ref(null);
const ellipsisDropdownPosition = reactive({ left: 0, top: 0 });
const hierarchyButton = ref(null);
const hierarchyDropdownPosition = reactive({ left: 0, top: 0 });
const isColorPaletteOpen = ref(false); // Ref for color palette visibility
const selectedColor = ref("#000000"); // Ref to store selected color

const editor = computed(() => props.editor);

const getClass = (type, attrs = {}) => {
  if (!editor.value) return "";
  return editor.value.isActive(type, attrs) ? "is-active" : "";
};

// Helper function to calculate dropdown position
const calculateDropdownPosition = (buttonRef, dropdownPositionReactive) => {
  if (buttonRef.value) {
    const buttonRect = buttonRef.value.getBoundingClientRect();
    dropdownPositionReactive.left = buttonRect.left;
    dropdownPositionReactive.top = buttonRect.bottom + window.scrollY; // Add scrollY to account for page scrolling
  }
};

// Functions to toggle dropdowns and calculate positions
const toggleEllipsisDropdown = () => {
  isEllipsisDropdownOpen.value = !isEllipsisDropdownOpen.value;
  if (isEllipsisDropdownOpen.value) {
    calculateDropdownPosition(ellipsisButton, ellipsisDropdownPosition);
    isHierarchyDropdownOpen.value = false; // Close other dropdown
    isColorPaletteOpen.value = false; // Close color palette if open
  }
};

const toggleHierarchyDropdown = () => {
  isHierarchyDropdownOpen.value = !isHierarchyDropdownOpen.value;
  if (isHierarchyDropdownOpen.value) {
    calculateDropdownPosition(hierarchyButton, hierarchyDropdownPosition);
    isEllipsisDropdownOpen.value = false; // Close other dropdown
    isColorPaletteOpen.value = false; // Close color palette if open
  }
};

// Hierarchy Dropdown Menu Functions
const setParagraph = () => {
  props.editor.chain().focus().setParagraph().run();
  isHierarchyDropdownOpen.value = false;
};

const setHeading = (level) => {
  props.editor.chain().focus().setHeading({ level: level }).run();
  isHierarchyDropdownOpen.value = false;
};

// Font and Style Functions
const setFontFamily = (font) => {
  props.editor.chain().focus().setFontFamily(font).run();
};

const setFontWeight = (weight) => {
  // "Medium" could be fontWeight: 500, or just default font-weight.  Using "500" for now as example.
  props.editor.chain().focus().setNodeAttribute("paragraph", "textStyle", { fontWeight: weight }).run();
  props.editor.chain().focus().setNodeAttribute("heading", "textStyle", { fontWeight: weight }).run();
};

// Basic Formatting Functions (already linked and working in template)
const insertLink = () => {
  const url = prompt("Enter the URL");
  if (url) {
    props.editor.chain().focus().setLink({ href: url }).run();
  }
};

const toggleHighlight = () => {
  props.editor.chain().focus().toggleHighlight().run();
};

// Color Palette Function
const toggleColorPalette = () => {
  isColorPaletteOpen.value = !isColorPaletteOpen.value;
  isEllipsisDropdownOpen.value = false; // Close other dropdown
  isHierarchyDropdownOpen.value = false; // Close other dropdown
};

const setColor = (color) => {
  selectedColor.value = color;
  props.editor.chain().focus().setColor(color).run();
  isColorPaletteOpen.value = false; // Close color palette after selecting color
};

const palette = () => {
  toggleColorPalette();
};

const insertHorizontalRule = () => {
  props.editor.chain().focus().setHorizontalRule().run();
};

// List Functions (Dropdown menu already linked)
const toggleBulletList = () => {
  props.editor.chain().focus().toggleBulletList().run();
  isHierarchyDropdownOpen.value = false;
};

const toggleOrderedList = () => {
  props.editor.chain().focus().toggleOrderedList().run();
  isHierarchyDropdownOpen.value = false;
};
</script>

<style scoped>
button.is-active {
  background-color: #0000001a;
  color: black;
}
@media (prefers-color-scheme: dark) {
  button.is-active {
    background-color: #373737;
    color: white;
  }
}
.btnBase {
  @apply flex items-center justify-center border text-sm font-semibold rounded-md disabled:opacity-50 whitespace-nowrap bg-transparent border-transparent text-neutral-500 dark:text-neutral-400 hover:bg-black/5 hover:text-neutral-700 active:bg-black/10 active:text-neutral-800 dark:hover:bg-white/10 dark:hover:text-neutral-300 dark:active:text-neutral-200 h-8 gap-1 min-w-[2rem] px-2 w-auto;
}

.dropdownBtn {
  @apply flex items-center gap-2 p-1.5 text-sm font-medium text-neutral-500 dark:text-neutral-400 text-left bg-transparent w-full rounded hover:bg-neutral-100 hover:text-neutral-800 dark:hover:bg-neutral-900 dark:hover:text-neutral-200;
}
</style>

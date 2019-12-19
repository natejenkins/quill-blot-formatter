// @flow

import {Aligner} from './Aligner'
import type {Alignment} from './Alignment'
import type {AlignOptions} from '../../Options'

const LEFT_ALIGN = 'left'
const CENTER_ALIGN = 'center'
const RIGHT_ALIGN = 'right'
const FULL_ALIGN = 'full'

export default class DefaultAligner implements Aligner {
  alignments: {[string]: Alignment}
  alignAttribute: string
  applyStyle: boolean

  constructor(options: AlignOptions) {
    this.applyStyle = options.aligner.applyStyle
    this.alignAttribute = options.attribute
    this.alignments = {
      [LEFT_ALIGN]: {
        name: LEFT_ALIGN,
        icon: options.icons.left,
        apply: (el: HTMLElement) => {
          el.setAttribute('style', '')
          this.setAlignment(el, LEFT_ALIGN)
          this.setStyle(el, 'inline', 'left', '0 1em 1em 0')
        },
      },
      [CENTER_ALIGN]: {
        name: CENTER_ALIGN,
        icon: options.icons.center,
        apply: (el: HTMLElement) => {
          el.setAttribute('style', '')
          this.setAlignment(el, CENTER_ALIGN)
          this.setStyle(el, 'block', null, 'auto')
        },
      },
      [RIGHT_ALIGN]: {
        name: RIGHT_ALIGN,
        icon: options.icons.right,
        apply: (el: HTMLElement) => {
          el.setAttribute('style', '')
          this.setAlignment(el, RIGHT_ALIGN)
          this.setStyle(el, 'inline', 'right', '0 0 1em 1em')
        },
      },
      [FULL_ALIGN]: {
        name: FULL_ALIGN,
        icon: options.icons.full,
        apply: (el: HTMLElement) => {
          console.info("FULL ALIGN 3")
          this.clear(el)
          // this.setAlignment(el, FULL_ALIGN)
          // this.setStyle(el, 'block', null, 'auto')
          el.setAttribute('width', `100%`)
          el.setAttribute('height', `100%`)
          el.setAttribute('style', 'position: absolute; left: 0; top: 0;')
        },
      },
    }
  }

  getAlignments(): Alignment[] {
    return Object.keys(this.alignments).map(k => this.alignments[k])
  }

  clear(el: HTMLElement): void {
    el.removeAttribute(this.alignAttribute)
    this.setStyle(el, null, null, null)
  }

  isAligned(el: HTMLElement, alignment: Alignment): boolean {
    return el.getAttribute(this.alignAttribute) === alignment.name
  }

  setAlignment(el: HTMLElement, value: string) {
    el.setAttribute(this.alignAttribute, value)
  }

  setStyle(el: HTMLElement, display: ?string, float: ?string, margin: ?string) {
    if (this.applyStyle) {
      el.style.setProperty('display', display)
      el.style.setProperty('float', float)
      el.style.setProperty('margin', margin)
    }
  }

  // clearStyle(el: HTMLElement) {
  //   if (this.applyStyle) {
  //     el.style.
  //   }
  // }
}

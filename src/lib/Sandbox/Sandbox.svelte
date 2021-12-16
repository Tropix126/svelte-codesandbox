<script lang="ts">
    /** Sandbox ID to be embedded */
    export let src = "new";

    /** Specifies a feature policy for the <iframe>. */
    export let allow = "accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking";

    /** Title of the <iframe> used for accessibility purposes */
    export let title = "Sandbox";

    /** Automatically resize the embed to the content (only works on Medium). */
    export let autoResize = false;

    /** Use CodeMirror editor instead of Monaco (decreases embed size significantly). */
    export let codemirror = false;

    /** Size in percentage of editor. */
    export let editorSize = 50;

    /** Use eslint (increases embed size significantly). */
    export let eslint = false;

    /** Start with the devtools (console) open. */
    export let expandDevtools = false;

    /** Hide the DevTools bar of the preview. */
    export let hideDevtools = false;

    /** Font size of editor */
    export let fontSize = 14;

    /** Force a full refresh of frame after every edit. */
    export let forceRefresh = 0;

    /** Hide the navigation bar of the preview. */
    export let hideNavigation = false;

    /** Which lines to highlight (only works in CodeMirror) */
    export let highlights: number[] = undefined;

    /** Which url to initially load in address bar */
    export let initialPath = "/";

    /** Which module to open by default. Multiple paths comma separated are allowed, in that case we show them as tabs */
    export let module: string[] | string = initialPath;

    /** Evaluate the file that is open in the editor. */
    export let moduleView = false;

    /** Which preview window to open by default */
    export let previewWindow: "console" | "tests" | "browser" = "browser";

    /** Only load the preview when the user says so. */
    export let runOnClick = false;

    /** Which view to open by default */
    export let view: "editor" | "split" | "preview" | "auto" = "auto";

    /** Which theme to show for the embed */
    export let theme: "dark" | "light" = "dark";

    /** Custom class name to be applied to the sandbox <iframe> */
    let className = "";
    export { className as class };

    const EMBED_BASE = "https://codesandbox.io/embed";

    $: queryString = new URLSearchParams({
        autoresize: +autoResize,
        codemirror: +codemirror,
        editorsize: editorSize,
        eslint: +eslint,
        expanddevtools: +expandDevtools,
        hidedevtools: +hideDevtools,
        // @ts-ignore
        fontsize: fontSize,
        forcerefresh: +forceRefresh,
        hidenavigation: +hideNavigation,
        highlights: highlights?.toString() ?? "",
        initialpath: initialPath,
        module: Array.isArray(module) ? module?.toString() ?? "/" : module,
        moduleview: +moduleView,
        previewwindow: previewWindow,
        runonclick: +runOnClick,
        theme,
        view
    });
</script>

<!--
@component
Wrapper component around the [CodeSandbox editor embed](https://codesandbox.io/docs/embedding) \<iframe>\.

- Basic Usage:
    ```tsx
    <Sandbox src="sandbox-id" />
    ```
-->
<iframe
    class="sandbox {className ?? ''}"
    src="{EMBED_BASE}/{src}?{queryString.toString()}"
    sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
    {title}
    {allow}
    {...$$restProps}
/>

<style lang="scss">
    @use "./Sandbox";
</style>
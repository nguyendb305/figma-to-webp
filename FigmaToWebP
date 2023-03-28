figma.showUI(__html__);
  
async function exportFrameToWebP(frameNode) {
  const options = { format: 'WEBP', constraint: { type: 'ORIGINAL' } };
  const bytes = await frameNode.exportAsync(options);
  const arrayBuffer = await bytes.arrayBuffer();
  const file = new Blob([arrayBuffer], { type: 'image/webp' });
  return URL.createObjectURL(file);
}

figma.ui.onmessage = async (msg) => {
  if (msg.type === 'exportFrameToWebP') {
    const { frameId } = msg;
    const frameNode = figma.getNodeById(frameId);
    const url = await exportFrameToWebP(frameNode);
    figma.ui.postMessage({ type: 'webpExported', url });
  }
};

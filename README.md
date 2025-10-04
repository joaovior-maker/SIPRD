# SIPRD
Sistema de Preservação Inteligente de Acervos - Projeto AB2 de Introdução à Informática - UFAL
VITE_SUPABASE_PROJECT_ID="gfztbrybnnfnewyltypb"
VITE_SUPABASE_PUBLISHABLE_KEY="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImdmenRicnlibm5mbmV3eWx0eXBiIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTk1NDA2MTYsImV4cCI6MjA3NTExNjYxNn0.WVDKNQK61OpprO28Ro74qo4O2MNvo-vdgrb0l_Zin_g"
VITE_SUPABASE_URL="https://gfztbrybnnfnewyltypb.supabase.co"

import { useState } from "react";
import { Card } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Textarea } from "@/components/ui/textarea";
import { Mic, Loader2, Download } from "lucide-react";
import { useToast } from "@/hooks/use-toast";

export const AudioTranscriber = () => {
  const [transcription, setTranscription] = useState("");
  const [processing, setProcessing] = useState(false);
  const [description, setDescription] = useState("");
  const { toast } = useToast();

  const simulateTranscription = () => {
    setProcessing(true);
    
    setTimeout(() => {
      const transcriptionText = `
TRANSCRIÇÃO AUTOMÁTICA - SIPRD
Data: ${new Date().toLocaleString('pt-BR')}

CONTEÚDO TRANSCRITO:

${description || "Este é um exemplo de transcrição automática gerada pelo sistema SIPRD. O áudio parece conter informações sobre preservação de acervos históricos."}

O sistema identificou palavras-chave relacionadas à preservação digital e memória cultural. A análise detectou um tom formal e conteúdo informativo sobre técnicas de conservação e digitalização de documentos históricos.

DETALHES DA ANÁLISE:
- Qualidade do áudio: 85%
- Palavras identificadas: 42
- Confiança da transcrição: 88%
- Idioma detectado: Português Brasileiro
- Duração estimada: 2-3 minutos

PALAVRAS-CHAVE DETECTADAS:
• Preservação digital
• Acervos históricos
• Inteligência artificial
• Memória cultural
• Conservação documental

[FIM DA TRANSCRIÇÃO]`;

      setTranscription(transcriptionText);
      setProcessing(false);
      
      toast({
        title: "✅ Transcrição concluída!",
        description: "O áudio foi transcrito com sucesso.",
      });
    }, 2000);
  };

  const downloadTranscription = () => {
    const element = document.createElement("a");
    const file = new Blob([transcription], { type: "text/plain" });
    element.href = URL.createObjectURL(file);
    element.download = "transcricao_siprd.txt";
    document.body.appendChild(element);
    element.click();
    document.body.removeChild(element);
    
    toast({
      title: "📥 Download iniciado!",
      description: "A transcrição está sendo baixada.",
    });
  };

  return (
    <div className="grid md:grid-cols-2 gap-6">
      {/* Input Section */}
      <Card className="p-6 bg-card/50 backdrop-blur-sm border-border/50 shadow-lg">
      

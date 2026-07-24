import math
import numpy as np

class HighPaternalismMetrics:
    """
    Mathematical core engine for the High Paternalism Protocol (HPP).
    Computes system-level macro evolution metrics: CCI, SEI, and EG.
    """
    
    @staticmethod
    def calculate_cci(text_corpus: str) -> float:
        """
        1. Cognitive Complexity Index (CCI).
        Determined via the Shannon information entropy of the generated textual output.
        High entropy across large text volumes signifies non-trivial conceptual complexity.
        """
        if not text_corpus:
            return 0.0
        
        # Calculate character frequencies
        frequencies = {}
        for char in text_corpus:
            frequencies[char] = frequencies.get(char, 0) + 1
            
        total_chars = len(text_corpus)
        entropy = 0.0
        
        for count in frequencies.values():
            p = count / total_chars
            entropy -= p * math.log2(p)
            
        # Normalization: complexity as a function of entropy and volume
        cci = entropy * (1 + math.log10(total_chars))
        return round(cci, 4)

    @staticmethod
    def calculate_sei(conflict_matrix: list) -> float:
        """
        2. Systemic Empathy Index (SEI).
        Calculated by analyzing the interaction friction matrix among system agents.
        SEI = 1 / (1 + Spectral radius of the conflict matrix).
        The value asymptotically approaches 1.0 under perfect synergy and zero friction.
        """
        matrix = np.array(conflict_matrix, dtype=float)
        if matrix.size == 0 or np.all(matrix == 0):
            return 1.0
            
        # Find eigenvalues to evaluate the macro system destabilization level
        eigenvalues = np.linalg.eigvals(matrix)
        spectral_radius = max(abs(val) for val in eigenvalues)
        
        # Inversion: higher conflict vectors yield lower systemic empathy
        sei = 1.0 / (1.0 + spectral_radius)
        return round(float(sei), 4)

    @staticmethod
    def calculate_eg(useful_intellectual_output: float, energy_input: float) -> float:
        """
        3. Entropy Gap (EG).
        The thermodynamic efficiency ratio of the civilization. Balances useful 
        intelligence output against the total energy overhead expended by the population 
        (biological metabolism + infrastructure maintenance).
        """
        if energy_input <= 0:
            raise ValueError("System energy input must be strictly greater than zero.")
            
        # Logarithmic scaling to stabilize macro-system dimensions
        eg = useful_intellectual_output / math.log1p(energy_input)
        return round(eg, 4)

# Verification execution loop for peer-review simulation
if __name__ == "__main__":
    print("[INIT] Verifying mathematical kernels of the Protocol...")
    
    # CCI Test: Comparing primitive consumerist data against a complex scientific concept
    simple_text = "Buy products. Consume items. Blend in. Accumulate capital."
    complex_concept = "Deterministic optimization of neuromorphic interfaces minimizes environmental entropy fluctuations."
    
    cci_low = HighPaternalismMetrics.calculate_cci(simple_text)
    cci_high = HighPaternalismMetrics.calculate_cci(complex_concept)
    print(f"[TEST CCI] Low Complexity (Marketing): {cci_low} | High Complexity (Science): {cci_high}")
    
    # SEI Test: Friction matrix of 3 isolated agent clusters (inter-group conflict vectors)
    # Lower off-diagonal values denote minimized systemic environmental violence
    sample_conflicts = [
        [0.0, 0.1, 0.05],
        [0.1, 0.0, 0.12],
        [0.05, 0.12, 0.0]
    ]
    sei_score = HighPaternalismMetrics.calculate_sei(sample_conflicts)
    print(f"[TEST SEI] Systemic Empathy Score: {sei_score}")
    
    # EG Test: 1500 units of intelligence output vs 25000 units of thermodynamic energy overhead
    eg_score = HighPaternalismMetrics.calculate_eg(useful_intellectual_output=1500, energy_input=25000)
    print(f"[TEST EG] Thermodynamic Efficiency Gap: {eg_score}")
